class Auto
{
    private string markauto;
    private float startautoX;
    private float startautoY;
    private float speedauto;
    public Auto()
    {
        markauto = "Неопознаный Едущий Объект";
        startautoX = 0.0f;
        startautoY = 0.0f;
        speedauto = 0.0f;
    }
    public Auto(string mark, float startX, float startY, float speed)
    {
        markauto = mark;
        startautoX = startX;
        startautoY = startY;
        speedauto = speed;
    }
    public void Info()
    {
        Console.WriteLine($"Марка: {markauto}, Координаты: X={startautoX}, Y={startautoY}, Скорость(начальная): {speedauto} км/ч");
    }
    public void Move(float dx, float dy)
    {
        startautoX += dx;
        startautoY += dy;
        Console.WriteLine($"Новые координаты: X={startautoX}, Y={startautoY}");
    }
    public void uskor(float value)
    {
        speedauto = speedauto + value;
        Console.WriteLine($"Ускорение: новая скорость {speedauto} км/ч");
    }
    public void tormoz(float value)
    {
        speedauto = speedauto - value;
        if (speedauto < 0) speedauto = 0;
        Console.WriteLine($"Торможение: новая скорость {speedauto} км/ч");
    }
    public void MoveBySpeed(float seconds)
    {
        float metersPerSecond = speedauto * 1000 / 3600;
        float distance = metersPerSecond * seconds;
        startautoX += distance;
        Console.WriteLine($"Перемещено на основе скорости: X={startautoX}, Y={startautoY}, Пройденное расстояние: {distance:F2} м за {seconds} с.");
    }
}
class Program
{
    static void Main(string[] args)
    {
        Auto car1 = new Auto();
        Auto car2 = new Auto("Красный Трактор", 2.0f, 5.0f, 6f);
        Auto car3 = new Auto("Автобус", 1.0f, 1.0f, 4f);
        Auto car4 = new Auto("Зеленый Автомобиль", 0.0f, 0.0f, 0.0f);
        Auto car5 = new Auto("Танк", 100.0f, 20.0f, 60.0f);
        car1.Info();
        car1.uskor(9f);
        car1.MoveBySpeed(10);
        Console.WriteLine();
        car2.Info();
        car2.uskor(35f);
        car2.MoveBySpeed(5);
        Console.WriteLine();
        car3.Info();
        car3.tormoz(2f);
        car3.MoveBySpeed(15);
        Console.WriteLine();
        car4.Info();
        car4.uskor(80f);
        car4.MoveBySpeed(150);
        Console.WriteLine();
        car5.Info();
        car5.tormoz(10f);
        car5.MoveBySpeed(150000);
    }
}
