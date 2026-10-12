# Console_Game_Massive
```csharp
using System;

class Program
{
    static void Main()
    {
        Console.OutputEncoding = System.Text.Encoding.UTF8;

        Console.WriteLine("=== ДРЕВНЕРУССКАЯ ЗАСТАВА: БОГАТЫРСКИЙ ДОЗОР ===\n");

        
        // Задание 1. Строковый массив богатырского снаряжения на 5 слотов
        
        string[] gear = { "Булатный меч", "Кованый щит", "Колчан каленых стрел", "Горбушка хлеба", "Шелковый шатер" };

        Console.WriteLine("--- Снаряжение богатыря ---");
        foreach (string item in gear)
        {
            Console.WriteLine($"[Снаряжение] {item}");
        }
        Console.WriteLine();

        
        // Задание 2. Три параллельных массива для вражеских сил
        
        string[] enemies = { "Степной дозорный", "Лесной разбойник", "Степной хан" };
        int[] warriors = { 35, 65, 130 };      // число воинов в сотне (HP)
        int[] fury = { 12, 28, 55 };           // боевая ярость (урон)

        Console.WriteLine("--- Супостаты на пути ---");
        for (int i = 0; i < enemies.Length; i++)
        {
            Console.WriteLine($"{i + 1}. {enemies[i]} | воинов: {warriors[i]} | ярость: {fury[i]}");
        }
        Console.WriteLine();

        
        // Задание 3. Массив верст патрулирования границы
        
        int[] verstsCovered = { 15, 22, 18, 30, 25 };

        
        // Задание 4. Вывод перечня снаряжения через foreach (уже выше)
        

        
        // Задание 5. Поиск "Кованый щит" через Array.IndexOf
        
        int shieldIndex = Array.IndexOf(gear, "Кованый щит");
        if (shieldIndex != -1)
        {
            Console.WriteLine($"Щит найден в слоте {shieldIndex + 1}. Богатырь готов отразить стрелковый залп!");
        }
        else
        {
            Console.WriteLine("Щита нет — придется укрываться за булатным мечом!");
        }
        Console.WriteLine();

        
        // Задание 6. Массив силы богатырских ударов на 5 раундов сечи
        
        int[] strikePowerLog = { 24, 41, 17, 55, 33 };

        Console.WriteLine("--- Лог силы ударов по раундам ---");
        for (int i = 0; i < strikePowerLog.Length; i++)
        {
            Console.WriteLine($"Раунд {i + 1}: удар силой {strikePowerLog[i]}");
        }
        Console.WriteLine();

        
        // Задание 7. Суммарный богатырский урон (ручной цикл for)
        
        int totalStrike = 0;
        for (int i = 0; i < strikePowerLog.Length; i++)
        {
            totalStrike += strikePowerLog[i];
        }
        Console.WriteLine($"Суммарный богатырский урон за сечу: {totalStrike}\n");

        
        // Задание 8. Самый дальний выезд (максимум верст)
        
        int maxVerst = verstsCovered[0];
        int maxDay = 0;
        for (int i = 1; i < verstsCovered.Length; i++)
        {
            if (verstsCovered[i] > maxVerst)
            {
                maxVerst = verstsCovered[i];
                maxDay = i;
            }
        }
        Console.WriteLine($"Самый дальний выезд: день {maxDay + 1}, {maxVerst} верст\n");

        
        // Задание 9. Сортировка массива ударов по возрастанию (Array.Sort)
        
        Array.Sort(strikePowerLog);
        Console.WriteLine("Сила ударов по возрастанию: " + string.Join(", ", strikePowerLog));
        Console.WriteLine($"Слабейший удар: {strikePowerLog[0]}");
        Console.WriteLine($"Мощнейший удар: {strikePowerLog[strikePowerLog.Length - 1]}\n");

        
        // Задание 10. Разворот массива верст (Array.Reverse) — обратный путь
        
        Array.Reverse(verstsCovered);
        Console.WriteLine("Обратный путь на заставу (версты по дням): " + string.Join(" -> ", verstsCovered));

        Console.WriteLine("\n=== Дозор завершен. Слава Руси! ===");
    }
}
```

<img width="979" height="512" alt="изображение" src="https://github.com/user-attachments/assets/8740c34d-f9a7-4685-86b3-3653c5c4d844" />
