3 завд 
public class Money {
    private int whole;  // Ціла частина (гривні, долари, євро)
    private int cents;  // Копійки, цента, євроценти

    // Конструктор для ініціалізації суми
    public Money(int whole, int cents) {
        this.whole = whole;
        this.cents = cents;
        adjust();
    }

    // Коригує значення копійок, щоб їх було менше 100
    private void adjust() {
        if (cents >= 100) {
            whole += cents / 100;
            cents = cents % 100;
        }
    }

    // Виведення суми
    public void showAmount() {
        System.out.println(whole + " одиниць і " + cents + " копійок.");
    }

    // Метод для зменшення суми на певну кількість копійок
    public void decrease(int amountInCents) {
        int totalCents = whole * 100 + cents - amountInCents;
        whole = totalCents / 100;
        cents = totalCents % 100;
        adjust();
    }
}

Клас Product

public class Product {
    private String name;  // Назва продукту
    private Money price;  // Ціна продукту

    // Конструктор для ініціалізації продукту
    public Product(String name, Money price) {
        this.name = name;
        this.price = price;
    }

    // Виведення інформації про продукт
    public void showProductInfo() {
        System.out.print("Продукт: " + name + ", ціна: ");
        price.showAmount();
    }

    // Зменшення ціни на певну кількість копійок
    public void discount(int amountInCents) {
        price.decrease(amountInCents);
    }
}

Як використати 

public class Main {
    public static void main(String[] args) {
        // Створення грошей для ціни товару
        Money itemPrice = new Money(120, 50); // 120 одиниць і 50 копійок

        // Створення продукту
        Product product = new Product("Ноутбук", itemPrice);

        // Виведення інформації про продукт
        product.showProductInfo();

        // Знижка на товар
        product.discount(50); // Зменшуємо ціну на 50 копійок

        // Виведення нової ціни
        System.out.println("\nПісля знижки:");
        product.showProductInfo();
    }
}
4 завд
Базовий клас Device
// Базовий клас "Пристрій"
public class Device {
    String name;  // Назва пристрою
    String description;  // Опис пристрою

    // Конструктор для ініціалізації
    public Device(String name, String description) {
        this.name = name;
        this.description = description;
    }

    // Метод для звуку пристрою
    public void sound() {
        System.out.println(name + " не видає звуку.");
    }

    // Метод для показу назви пристрою
    public void show() {
        System.out.println("Пристрій: " + name);
    }

    // Метод для опису пристрою
    public void desc() {
        System.out.println("Опис: " + description);
    }
}
Клас Teapot
// Клас "Чайник"
public class Teapot extends Device {
    
    public Teapot(String name, String description) {
        super(name, description);
    }

    // Перевизначений метод для звуку чайника
    @Override
    public void sound() {
        System.out.println(name + " свистить!");
    }

    // Опис для чайника
    @Override
    public void desc() {
        System.out.println(name + " - це прилад для кип'ятіння води.");
    }
}
Клас Microwave
// Клас "Мікрохвильовка"
public class Microwave extends Device {

    public Microwave(String name, String description) {
        super(name, description);
    }

    // Перевизначений метод для звуку мікрохвильовки
    @Override
    public void sound() {
        System.out.println(name + " бібікає!");
    }

    // Опис для мікрохвильовки
    @Override
    public void desc() {
        System.out.println(name + " використовується для швидкого розігріву їжі.");
    }
}

Клас Car
// Клас "Автомобіль"
public class Car extends Device {

    public Car(String name, String description) {
        super(name, description);
    }

    // Перевизначений метод для звуку автомобіля
    @Override
    public void sound() {
        System.out.println(name + " реве на дорозі!");
    }

    // Опис для автомобіля
    @Override
    public void desc() {
        System.out.println(name + " - транспортний засіб для перевезення людей.");
    }
}

Клас Steamship
// Клас "Пароплав"
public class Steamship extends Device {

    public Steamship(String name, String description) {
        super(name, description);
    }

    // Перевизначений метод для звуку пароплава
    @Override
    public void sound() {
        System.out.println(name + " гудить на воді!");
    }

    // Опис для пароплава
    @Override
    public void desc() {
        System.out.println(name + " - це великий судно для перевезення людей по воді.");
    }
}

Приклад використання

public class Main {
    public static void main(String[] args) {
        // Створення об'єктів для кожного пристрою
        Device teapot = new Teapot("Чайник", "Пристрій для кип'ятіння води");
        Device microwave = new Microwave("Мікрохвильовка", "Пристрій для швидкого розігріву їжі");
        Device car = new Car("Автомобіль", "Транспортний засіб для перевезення людей");
        Device steamship = new Steamship("Пароплав", "Водний транспорт для перевезення людей");

        // Виклик методів для кожного пристрою
        teapot.show();
        teapot.desc();
        teapot.sound();

        System.out.println();

        microwave.show();
        microwave.desc();
        microwave.sound();

        System.out.println();

        car.show();
        car.desc();
        car.sound();

        System.out.println();

        steamship.show();
        steamship.desc();
        steamship.sound();
    }
}
