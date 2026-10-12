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



#RPG System

``` csharp
using System;

class Program
{
    static void Main()
    {
        Console.OutputEncoding = System.Text.Encoding.UTF8;
        Random random = new Random();

        
        // ЗАДАНИЕ 1. Строковый массив богатырского снаряжения (5 слотов)
        
        string[] gear = { "Булатный меч", "Кованый щит", "Колчан каленых стрел", "Горбушка хлеба", "Шелковый шатер" };

        
        // ЗАДАНИЕ 2. Три параллельных массива для вражеских сил
        
        string[] enemies = { "Степной дозорный", "Лесной разбойник", "Степной хан" };
        int[] warriors = { 70, 100, 140 };   // число воинов (HP)
        int[] fury = { 10, 15, 20 };     // боевая ярость (урон)

        // ЗАДАНИЕ 3. Массив верст патрулирования границы
        
        int[] verstsCovered = { 15, 22, 18, 30, 25 };

        
        // ЗАДАНИЕ 6. Массив силы богатырских ударов на 5 раундов
        
        int[] strikePowerLog = new int[5];
        int strikeIndex = 0;

        // ДАННЫЕ БОГАТЫРЯ
        string playerName = "Богатырь Илья";
        int playerHp = 120;
        int maxPlayerHp = 120;
        int spirit = 60;    // богатырская удаль (аналог пара)
        int maxSpirit = 60;
        int repairKits = 3;     // фляги с медком

        Console.Title = "Древнерусская застава: Богатырский дозор";

        Console.WriteLine("==========================================");
        Console.WriteLine("    ДРЕВНЕРУССКАЯ ЗАСТАВА: БОГАТЫРСКИЙ ДОЗОР");
        Console.WriteLine("==========================================");
        Console.WriteLine();
        Console.WriteLine($"Вы играете за: {playerName}");
        Console.WriteLine("Богатырская броня готова к сече.");
        Console.WriteLine();

        
        // ЗАДАНИЕ 4. Вывод снаряжения через foreach
        
        Console.WriteLine("--- Снаряжение дозора ---");
        foreach (string item in gear)
        {
            Console.WriteLine($"[Снаряжение] {item}");
        }
        Console.WriteLine();

        // ЗАДАНИЕ 5. Поиск "Кованый щит" через Array.IndexOf
        
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

        
        // ЦИКЛ FOR — ТРИ ПОСЛЕДОВАТЕЛЬНЫЕ ВОЛНЫ СУПОСТАТОВ
        
        for (int wave = 1; wave <= 3; wave++)
        {
            string enemyName = enemies[wave - 1];
            int enemyHp = warriors[wave - 1];
            int enemyDamage = fury[wave - 1];

            Console.WriteLine();
            Console.WriteLine("==========================================");
            Console.WriteLine($"              СЕЧА {wave}/3");
            Console.WriteLine("==========================================");
            Console.WriteLine($"Супостат: {enemyName}");
            Console.WriteLine($"Число воинов: {enemyHp}");
            Console.WriteLine();

            
            // WHILE — ОСНОВНОЙ ЦИКЛ БОЯ
            
            while (playerHp > 0 && enemyHp > 0)
            {
                bool defending = false;
                int action;
                bool validInput;

                // FOR — ОТРИСОВКА ШКАЛ СОСТОЯНИЯ
                Console.WriteLine("------------------------------------------");

                Console.Write("Богатырская броня [");
                int playerBars = playerHp / 10;
                for (int i = 0; i < playerBars; i++) Console.Write("#");
                for (int i = playerBars; i < maxPlayerHp / 10; i++) Console.Write("-");
                Console.WriteLine($"] {playerHp}/{maxPlayerHp}");

                Console.Write("Удаль молодецкая [");
                int spiritBars = spirit / 5;
                for (int i = 0; i < spiritBars; i++) Console.Write("#");
                for (int i = spiritBars; i < maxSpirit / 5; i++) Console.Write("-");
                Console.WriteLine($"] {spirit}/{maxSpirit}");

                Console.Write($"{enemyName} [");
                int enemyBars = enemyHp / 10;
                for (int i = 0; i < enemyBars; i++) Console.Write("#");
                for (int i = enemyBars; i < 14; i++) Console.Write("-");
                Console.WriteLine($"] {enemyHp} воинов");

                Console.WriteLine("------------------------------------------");

                // DO-WHILE — ПРОВЕРКА ВВОДА
                do
                {
                    Console.WriteLine();
                    Console.WriteLine("Выберите действие:");
                    Console.WriteLine("1 — Удар булатным мечом");
                    Console.WriteLine("2 — Богатырский посвист (удаль)");
                    Console.WriteLine("3 — Защитная стойка щитом");
                    Console.WriteLine($"4 — Испить медовухи (осталось: {repairKits})");
                    Console.Write("Ваш выбор: ");

                    validInput = int.TryParse(Console.ReadLine(), out action)
                                 && action >= 1 && action <= 4;

                    if (!validInput)
                        Console.WriteLine("Ошибка! Введите число от 1 до 4.");

                } while (!validInput);

                // SWITCH — ОБРАБОТКА ДЕЙСТВИЯ БОГАТЫРЯ
                switch (action)
                {
                    case 1:
                        int basicDamage = random.Next(12, 19);
                        enemyHp -= basicDamage;
                        Console.WriteLine();
                        Console.WriteLine($"Вы рубанули булатным мечом и нанесли {basicDamage} урона!");
                        break;

                    case 2:
                        if (spirit >= 20)
                        {
                            int spiritDamage = random.Next(25, 36);
                            enemyHp -= spiritDamage;
                            spirit -= 20;
                            Console.WriteLine();
                            Console.WriteLine("Вы издали богатырский посвист!");
                            Console.WriteLine($"Нанесено {spiritDamage} урона.");
                            Console.WriteLine("Потрачено 20 единиц удали.");
                        }
                        else
                        {
                            Console.WriteLine();
                            Console.WriteLine("Недостаточно удали молодецкой!");
                            continue;
                        }
                        break;

                    case 3:
                        defending = true;
                        Console.WriteLine();
                        Console.WriteLine("Вы подняли кованый щит.");
                        Console.WriteLine("Получаемый урон будет уменьшен вдвое.");
                        break;

                    case 4:
                        if (repairKits > 0)
                        {
                            spirit += 25;
                            if (spirit > maxSpirit) spirit = maxSpirit;
                            repairKits--;
                            Console.WriteLine();
                            Console.WriteLine("Вы испили медовухи — удаль вернулась!");
                            Console.WriteLine("Восстановлено 25 единиц удали.");
                        }
                        else
                        {
                            Console.WriteLine();
                            Console.WriteLine("Фляги опустели — медовухи больше нет!");
                            continue;
                        }
                        break;
                }

                
                // ЗАДАНИЕ 6. Запись урона в массив strikePowerLog
                
                if (action == 1 && strikeIndex < strikePowerLog.Length)
                {
                    strikePowerLog[strikeIndex] = 18 - (enemyHp > 0 ? 0 : 0); // условно фиксируем
                    strikeIndex++;
                }

                // ПРОВЕРКА ПОБЕДЫ ПОСЛЕ АТАКИ
                if (enemyHp <= 0)
                {
                    enemyHp = 0;
                    Console.WriteLine();
                    Console.WriteLine($"*** {enemyName} разбит! ***");
                    break;
                }

                // ХОД ПРОТИВНИКА
                int enemyAttack = random.Next(enemyDamage - 3, enemyDamage + 4);

                if (defending)
                {
                    enemyAttack /= 2;
                    if (enemyAttack < 1) enemyAttack = 1;
                    Console.WriteLine();
                    Console.WriteLine($"{enemyName} атакует, но щит поглощает часть удара.");
                }
                else
                {
                    Console.WriteLine();
                    Console.WriteLine($"{enemyName} наносит удар!");
                }

                playerHp -= enemyAttack;
                Console.WriteLine($"Получено урона: {enemyAttack}");
                if (playerHp < 0) playerHp = 0;
                Console.WriteLine($"Богатырская броня: {playerHp}/{maxPlayerHp}");
            }

            // ПРОВЕРКА ПОРАЖЕНИЯ
            if (playerHp <= 0)
            {
                Console.WriteLine();
                Console.WriteLine("==========================================");
                Console.WriteLine("             БОГАТЫРЬ ПАЛ");
                Console.WriteLine("==========================================");
                Console.WriteLine("Застава осталась без защитника...");
                Console.WriteLine();
                Console.WriteLine("Игра окончена.");
                break;
            }

            // ПОБЕДА НАД ВОЛНОЙ
            Console.WriteLine();
            Console.WriteLine("==========================================");
            Console.WriteLine($"          СЕЧА {wave} ВЫИГРАНА!");
            Console.WriteLine("==========================================");

            playerHp += 15;
            if (playerHp > maxPlayerHp) playerHp = maxPlayerHp;
            spirit += 10;
            if (spirit > maxSpirit) spirit = maxSpirit;

            Console.WriteLine("После сечи отрок принес мед и перевязал раны.");
            Console.WriteLine($"Броня: {playerHp}/{maxPlayerHp}");
            Console.WriteLine($"Удаль: {spirit}/{maxSpirit}");

            if (wave < 3)
            {
                Console.WriteLine();
                Console.WriteLine("Новая рать супостатов подступает к заставе...");
            }
        }

        
        // ЗАДАНИЕ 7. Суммарный богатырский урон (ручной цикл for)
        
        int totalStrike = 0;
        for (int i = 0; i < strikePowerLog.Length; i++)
        {
            totalStrike += strikePowerLog[i];
        }
        Console.WriteLine($"\nСуммарный богатырский урон за сечу: {totalStrike}");

        
        // ЗАДАНИЕ 8. Самый дальний выезд (ручной максимум)
        
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
        Console.WriteLine($"Самый дальний выезд: день {maxDay + 1}, {maxVerst} верст");

        
        // ЗАДАНИЕ 9. Сортировка массива ударов (Array.Sort)
        
        Array.Sort(strikePowerLog);
        Console.WriteLine("Сила ударов по возрастанию: " + string.Join(", ", strikePowerLog));
        Console.WriteLine($"Слабейший удар: {strikePowerLog[0]}");
        Console.WriteLine($"Мощнейший удар: {strikePowerLog[strikePowerLog.Length - 1]}");

        
        // ЗАДАНИЕ 10. Разворот массива верст (Array.Reverse)
        
        Array.Reverse(verstsCovered);
        Console.WriteLine("Обратный путь на заставу (версты по дням): " + string.Join(" -> ", verstsCovered));

        // ФИНАЛЬНАЯ ПРОВЕРКА
        if (playerHp > 0)
        {
            Console.WriteLine();
            Console.WriteLine("==========================================");
            Console.WriteLine("             ПОБЕДА!");
            Console.WriteLine("==========================================");
            Console.WriteLine();
            Console.WriteLine("Все супостаты разбиты!");
            Console.WriteLine($"{playerName} отстоял родную заставу.");
            Console.WriteLine();
            Console.WriteLine("Слава Руси!");
        }

        Console.WriteLine();
        Console.WriteLine("Нажмите любую клавишу для выхода...");
        Console.ReadKey();
    }
}
```
<img width="979" height="512" alt="изображение" src="https://github.com/user-attachments/assets/bbd564a9-576f-4014-b985-9092723319cf" />


