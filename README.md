sing System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace FactoryApp {

  // Абстрактний клас для визначення інтерфейсу продукту
  abstract class Motorcycle {
    public abstract string DisplayInfo();
  }

  // Конкретні класи продуктів
  class SportsBike : Motorcycle {
    public override string DisplayInfo() {
      return "Sports Bike: Fast and Agile";
    }
  }

  class Cruiser : Motorcycle {
    public override string DisplayInfo() {
      return "Cruiser: Comfortable and Stylish";
    }
  }

  class StreetBike : Motorcycle {
    public override string DisplayInfo() {
      return "Street Bike: Versatile and Practical";
    }
  }

  class AdventureTourer : Motorcycle {
    public override string DisplayInfo() {
      return "Adventure Tourer: Rugged and Ready for Long Journeys";
    }
  }

  // Абстрактний клас для визначення інтерфейсу фабрики
  abstract class MotorcycleFactory {
    public abstract Motorcycle CreateMotorcycle();
  }

  // Конкретні фабрики
  class SportsBikeFactory : MotorcycleFactory {
    public override Motorcycle CreateMotorcycle() {
      return new SportsBike();
    }
  }

  class CruiserFactory : MotorcycleFactory {
    public override Motorcycle CreateMotorcycle() {
      return new Cruiser();
    }
  }

  class StreetBikeFactory : MotorcycleFactory {
    public override Motorcycle CreateMotorcycle() {
      return new StreetBike();
    }
  }

  class AdventureTourerFactory : MotorcycleFactory {
    public override Motorcycle CreateMotorcycle() {
      return new AdventureTourer();
    }
  }

  // Клас для клієнта
  class Customer {
    public string Name { get; set; }
    public Motorcycle OrderMotorcycle(MotorcycleFactory factory) {
      return factory.CreateMotorcycle();
    }
  }
  internal class Program {
    static void Main(string[] args) {
      // Створення фабрик для різних типів мотоциклів
      MotorcycleFactory sportsBikeFactory = new SportsBikeFactory();
      MotorcycleFactory cruiserFactory = new CruiserFactory();
      MotorcycleFactory streetBikeFactory = new StreetBikeFactory();
      MotorcycleFactory adventureTourerFactory = new AdventureTourerFactory();

      // Створення клієнта
      Customer customer = new Customer { Name = "John Doe" };

      // Клієнт замовляє різні типи мотоциклів
      Motorcycle sportsBike = customer.OrderMotorcycle(sportsBikeFactory);
      Motorcycle cruiser = customer.OrderMotorcycle(cruiserFactory);
      Motorcycle streetBike = customer.OrderMotorcycle(streetBikeFactory);
      Motorcycle adventureTourer = customer.OrderMotorcycle(adventureTourerFactory);

      // Виведення інформації про замовлені мотоцикли
      Console.WriteLine(sportsBike.DisplayInfo());
      Console.WriteLine(cruiser.DisplayInfo());
      Console.WriteLine(streetBike.DisplayInfo());
      Console.WriteLine(adventureTourer.DisplayInfo());
      Console.ReadKey();
    }
  }
}

