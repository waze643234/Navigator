```
using System;

namespace StrategyDemo
{
    
    public interface IRouteStrategy
    {
        void BuildRoute(string start, string end);
    }

    
    public class CarStrategy : IRouteStrategy
    {
        public void BuildRoute(string start, string end)
        {
            Console.WriteLine($"Маршрут на АВТО з '{start}' до '{end}': 15 хв (через шосе).");
        }
    }

    
    public class WalkingStrategy : IRouteStrategy
    {
        public void BuildRoute(string start, string end)
        {
            Console.WriteLine($"ПІШИЙ маршрут з '{start}' до '{end}': 1 год 10 хв (через парк).");
        }
    }

    
    public class BusStrategy : IRouteStrategy
    {
        public void BuildRoute(string start, string end)
        {
            Console.WriteLine($"Маршрут АВТОБУСОМ з '{start}' до '{end}': 30 хв (маршрут №42).");
        }
    }

    
    public class Navigator
    {
        private IRouteStrategy _strategy;

        
        public void SetStrategy(IRouteStrategy strategy)
        {
            _strategy = strategy;
        }

        public void ShowRoute(string start, string end)
        {
            _strategy.BuildRoute(start, end);
        }
    }

    class Program
    {
        static void Main()
        {
            Navigator navigator = new Navigator();

            
            navigator.SetStrategy(new CarStrategy());
            navigator.ShowRoute("Дім", "Університет");

            
            navigator.SetStrategy(new WalkingStrategy());
            navigator.ShowRoute("Дім", "Університет");

            
            navigator.SetStrategy(new BusStrategy());
            navigator.ShowRoute("Дім", "Університет");
        }
    }
}
