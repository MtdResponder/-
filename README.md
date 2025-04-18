//Отсортировать массив из 10 случайных чисел по возрастанию, используя Array.Sort().

{
    int[] cska = { 5, 3, 8, 1, 11, 12, 40, 52, 9, 32 };

    Array.Sort(cska);
    foreach (int n in cska)
        Console.WriteLine(n);
    int min = cska.First();
    int max = cska.Last();
    Console.WriteLine($"Минимум: {min}");
    Console.WriteLine($"Максимум: {max}");
}

//Написать свою реализацию сортировки пузырьком
{
    //метод обмена элементов
    void Swap(ref int elm1, ref int elm2)
    {
        int temp = elm1;
        elm1 = elm2;
        elm2 = temp;
    }
    //сортировка пузырьком
    int[] BubbleSort(int[] massive)
    {
        int len = massive.Length;
        for (int i = 1; i < len; i++)
        {
            for (int j = 0; j < len - i; j++)
            {
                if (massive[j] > massive[j + 1])
                {
                    Swap(ref massive[j], ref massive[j + 1]);
                }
            }
        }
        return massive;
    }
    Console.WriteLine("Сортировка пузырьком");
    string[] parts = Console.ReadLine()!.Split(new[] { " ", ",", ";" }, StringSplitOptions.RemoveEmptyEntries);
    var sort = new int[parts.Length];
    for (int i = 0; i < parts.Length; i++)
    {
        sort[i] = Convert.ToInt32(parts[i]);
    }

    Console.WriteLine("Отсортированный массив: {0}", string.Join(", ", BubbleSort(sort)));
}

//Ввести строку и вывести каждый символ на новой строке.

{
    var text = "normal map";
    foreach (var character in text)
    {
        Console.WriteLine(character);
    }
}

//Вывести длину введённой строки.

{
    Console.Write("Введите строку: ");
    string input = Console.ReadLine();
    int length = input.Length;

    Console.WriteLine("Длина введённой строки: " + length);
}

//Преобразовать строку в верхний регистр.

{
    {
        string text = "LeGaCytoPBR";
        Console.WriteLine(text.ToUpper()); // LeGaCytoPBR
    }
}

//. Разделить строку на слова и вывести их по одному.
{
    Console.Write("Введите строку: ");
    string input = Console.ReadLine();

    // Разделяем строку на слова по пробелам
    string[] slova = input.Split(' ');

    // Выводим каждое слово на новой строке
    foreach (string word in slova)
    {
        Console.WriteLine(word);
    }
}

//Найти и заменить все вхождения слова 

{
    string text = "Кот сидел на перилах, с перил упал Кот, только очень сильно";

    text = text.Replace("Кот", "Пёс");
    Console.WriteLine(text);    // Пёс
}

using System;

class Program
{
    static void Main()
    {
        while (true)
        {
            Console.WriteLine("Меню:");
            Console.WriteLine("1. Вычислить количество дней между датами");
            Console.WriteLine("2. Вычислить количество рабочих дней между датами");
            Console.WriteLine("3. Добавить рабочие дни к дате");
            Console.WriteLine("4. Выход");
            Console.Write("Выберите опцию: ");

            string choice = Console.ReadLine();
            switch (choice)
            {
                case "1":
                    Console.Write("Введите первую дату (гггг-мм-дд): ");
                    bool result1 = DateTime.TryParse(Console.ReadLine(), out DateTime date1);
                    if (!result1 )
                    {                                                 // Выводим сообщение о некорректном символе, выходим из функции и заходим повторно 
                        Console.WriteLine("Некорректный символ");
                        Main();
                    }
                    Console.Write("Введите вторую дату (гггг-мм-дд): ");
                    bool result2 = DateTime.TryParse(Console.ReadLine(), out DateTime date2);
                    if (!result2)
                    {                                                 // Выводим сообщение о некорректном символе, выходим из функции и заходим повторно 
                        Console.WriteLine("Некорректный символ");
                        Main();
                    }
                    Console.WriteLine($"Разница в днях: {DaysBetween(date1, date2)}\n");
                    break;
                case "2":
                    Console.Write("Введите первую дату (гггг-мм-дд): ");
                    bool resultStartDate = DateTime.TryParse(Console.ReadLine(), out DateTime startDate);
                    if (!resultStartDate)
                    {                                                 // Выводим сообщение о некорректном символе, выходим из функции и заходим повторно 
                        Console.WriteLine("Некорректный символ");
                        Main();
                    }
                    Console.Write("Введите вторую дату (гггг-мм-дд): ");
                    bool resutlEndDate = DateTime.TryParse(Console.ReadLine(), out DateTime endDate);
                    if (!resutlEndDate)
                    {                                                 // Выводим сообщение о некорректном символе, выходим из функции и заходим повторно 
                        Console.WriteLine("Некорректный символ");
                        Main();
                    }
                    Console.WriteLine($"Количество рабочих дней: {BusinessDaysBetween(startDate, endDate)}\n");
                    break;
                case "3":
                    return;
                default:
                    Console.WriteLine("Неверный ввод, попробуйте снова.\n");
                    break;
            }
        }
    }

    static int DaysBetween(DateTime date1, DateTime date2)
    {
        return Math.Abs((date2 - date1).Days);
    }

    static int BusinessDaysBetween(DateTime startDate, DateTime endDate)
    {
        int businessDays = 0;
        DateTime date = startDate;
        while (date <= endDate)
        {
            if (date.DayOfWeek != DayOfWeek.Saturday && date.DayOfWeek != DayOfWeek.Sunday)
            {
                businessDays++;
            }
            date = date.AddDays(1);
        }
        return businessDays;
    }

    static DateTime AddBusinessDays(DateTime date, int days)
    {
        int addedDays = 0;
        while (addedDays < days)
        {
            date = date.AddDays(1);
            if (date.DayOfWeek != DayOfWeek.Saturday && date.DayOfWeek != DayOfWeek.Sunday)
            {
                addedDays++;
            }
        }
        return date;
    }
}

using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Введите:" + "\nЦифру" + "\nБукву" + "\nСимвол");
        char chr = Console.ReadKey().KeyChar;
        Console.WriteLine(); // Переход на новую строку после ввода символа

        if (chr >= '0' && chr <= '9')
        {
            Console.WriteLine("Это: цифра");
        }
        else if (chr >= 'A' && chr <= 'Z')
        {
            Console.WriteLine("Это: заглавная буква");
        }
        else if (chr >= 'a' && chr <= 'z')
        {
            Console.WriteLine("Это: строчная буква");
        }
        else
        {
            Console.WriteLine("Это: спецсимвол");
        }
        Main();
    }
}

class Program
{
    static void Main()
    {
        int[] input = new int[3];
        for (int i = 0; i < 3; i++)
        {
            bool result = int.TryParse(Console.ReadLine(), out int value);
            if (!result)
            {
                Console.WriteLine("Некорректный символ");
                Main();
            }

            input[i] = value;
        }

        // Достаём числа из массива
        int side1 = input[0];
        int side2 = input[1];
        int side3 = input[2];

        // Проверяем, является ли треугольник равносторонним (все стороны равны)
        if (side1 == side2 && side2 == side3)
        {
            Console.WriteLine("Треугольник равносторонний");
        }
        // Проверяем, является ли треугольник равнобедренным (две стороны равны)
        else if (side1 == side2 || side1 == side3 || side2 == side3)
        {
            Console.WriteLine("Треугольник равнобедренный");
        }
        // Если ни одно из условий не выполнено, значит треугольник разносторонний
        else
        {
            Console.WriteLine("Треугольник разносторонний");
        }
        Main();
    }
}

using System;

class Program
{
    static void Main()
    {
        bool continueCalculating = true;

        while (continueCalculating)
        {
            // Запрашиваем у клиента два числа
            Console.Write("Введите первое число: ");
            double num1 = Convert.ToDouble(Console.ReadLine());

            Console.Write("Введите второе число: ");
            double num2 = Convert.ToDouble(Console.ReadLine());

            // Запрашиваем у клиента выбор оператора
            Console.Write("Введите оператор (+, -, *, /, %, ^): ");
            string operatorChoice = Console.ReadLine();

            double result = 0;

            // Выполняем выбранную операцию 
            switch (operatorChoice)
            {
                case "+":
                    result = num1 + num2;
                    break;
                case "-":
                    result = num1 - num2;
                    break;
                case "*":
                    result = num1 * num2;
                    break;
                case "/":
                    // Проверка деления на ноль
                    if (num2 != 0)
                    {
                        result = num1 / num2;
                    }
                    else
                    {
                        Console.WriteLine("Ошибка: поделить на ноль невозможно.");
                        continue;
                    }
                    break;
                case "%":
                    // Остаток от деления
                    result = num1 % num2;
                    break;
                case "^":
                    result = Math.Pow(num1, num2);
                    break;
                default:
                    Console.WriteLine("Ошибка: неверно указан оператор.");
                    continue;
            }

            // Вывод результата
            Console.WriteLine($"Результат:{result}");

            // Запрос на продолжение
            Console.Write("Желаете продолжить" + "\nДа?" + "\nНет?");
            string continueResponse = Console.ReadLine().ToLower();

            if (continueResponse != "да")
            {
                continueCalculating = false;
            }
        }
        Console.WriteLine("Программа завершена.");

    }
}

namespace Year
{
    class Program
    {
        static void Main(string[] args)
        {
            Zxc();
        }
        static void Zxc()
        {
            Console.WriteLine("1.Выберите время года" + "\nЗима - 1" + "\nВесна - 2" + "\nЛето - 3" + "\nОсень - 4");
            bool result = int.TryParse(Console.ReadLine(), out int type);
            if (!result)
            {
                Console.WriteLine("Некорректный символ");
                Zxc();
            }
            if (type == 1)
            {
                Winter();
            }
            else if (type == 2)
            {
                Spring();
            }
            else if (type == 3)
            {
                Summer();
            }
            else if (type == 4)
            {
                Autumun();
            }
            else
            {
                Console.WriteLine("Неверное значение");
                Zxc();
            }
        }
        static void Winter()
        {
            Console.WriteLine("Напишите число месяца", "(1-3):");
            bool result = int.TryParse(Console.ReadLine(), out int MonthW);
            if (!result)
            {
                Console.WriteLine("Некорректный символ");
                Winter();
            }
            switch (MonthW)
            {
                case 1: Console.WriteLine("Декабрь"); break;
                case 2: Console.WriteLine("Январь"); break;
                case 3: Console.WriteLine("Февраль"); break;
                default: Console.WriteLine("Ошибка. В сезоне - 3 месяца"); break;

            }
            Zxc();
        }
        static void Spring()
        {
            Console.WriteLine("Напишите число месяца", "(1-3):");
            bool result = int.TryParse(Console.ReadLine(), out int MonthS);
            if (!result)
            {
                Console.WriteLine("Некорректный символ");
                Spring();
            }
            switch (MonthS)
            {
                case 1: Console.WriteLine("Март"); break;
                case 2: Console.WriteLine("Апрель"); break;
                case 3: Console.WriteLine("Май"); break;
                default: Console.WriteLine("Ошибка. В сезоне - 3 месяца"); break;
            }
            Zxc();
        }
        static void Summer()
        {
            Console.WriteLine("Напишите число месяца", "(1-3):");
            bool result = int.TryParse(Console.ReadLine(), out int MonthSr);
            if (!result)
            {
                Console.WriteLine("Некорректный символ");
                Summer();
            }
            switch (MonthSr)
            {
                case 1: Console.WriteLine("Июнь"); break;
                case 2: Console.WriteLine("Июль"); break;
                case 3: Console.WriteLine("Август"); break;
                default: Console.WriteLine("Ошибка. В сезоне - 3 месяца"); break;
            }
            Zxc();
        }
        static void Autumun()
        {
            Console.WriteLine("Напишите число месяца", "(1-3):");
            bool result = int.TryParse(Console.ReadLine(), out int MonthA);
            if (!result)
            {
                Console.WriteLine("Некорректный символ");
                Autumun();
            }
            switch (MonthA)
            {
                case 1: Console.WriteLine("Cентябрь"); break;
                case 2: Console.WriteLine("Октябрь"); break;
                case 3: Console.WriteLine("Ноябрь"); break;
                default: Console.WriteLine("Ошибка. В сезоне - 3 месяца"); break;
            }
            Zxc();
        }

    }
}

using System;
using System.ComponentModel.Design;
using System.Xml.Linq;

namespace ConsoleApp1
{
    class Program
    {
        static void Main(string[] args)
        {
            Format();
        }
        static void Format()
        {
            Console.WriteLine("Какой формат времени вы хотите использовать? Единица - 12-ти часовой формат, Двойка - 24-часовой", "(1-2):");
            bool result = int.TryParse(Console.ReadLine(), out int hs);
            if (!result)
            {
                Console.WriteLine("Некорректный символ");
                Format();
            }
            if (hs == 1)
            {
                Drip1();
            }
            else if (hs == 2)
            {
                Drip2();
            }
        }

        static void Drip1()
        {
            bool running = true;
            while (running)
            {
                Console.WriteLine("1.Введите число от 0 до 23 чтобы вывести время", "(0-25)" + "\n Введите число 25 для выхода из программы" + "\nВведите число 24 для перехода к 24-ом часовом формату","(0-23):");
                bool result = int.TryParse(Console.ReadLine(), out int hour12); // Булиана для проверки корректности входящего значения
                if (!result)
                {                                                 // Выводим сообщение о некорректном символе, выходим из функции и заходим повторно 
                    Console.WriteLine("Некорректный символ");
                    Drip1();
                }

                switch (hour12)
                {
                    case 0: Console.WriteLine("12 PM"); break;
                    case 1: Console.WriteLine("1 PM"); break;
                    case 2: Console.WriteLine("2 PM"); break;
                    case 3: Console.WriteLine("3 PM"); break;
                    case 4: Console.WriteLine("4 PM"); break;
                    case 5: Console.WriteLine("5 PM"); break;
                    case 6: Console.WriteLine("6 PM"); break;
                    case 7: Console.WriteLine("7 PM"); break;
                    case 8: Console.WriteLine("8 PM"); break;
                    case 9: Console.WriteLine("9 PM"); break;
                    case 10: Console.WriteLine("10 PM"); break;
                    case 11: Console.WriteLine("11 PM"); break;
                    case 12: Console.WriteLine("12 AM"); break;
                    case 13: Console.WriteLine("1 AM"); break;
                    case 14: Console.WriteLine("2 AM"); break;
                    case 15: Console.WriteLine("3 AM"); break;
                    case 16: Console.WriteLine("4 AM"); break;
                    case 17: Console.WriteLine("5 AM"); break;
                    case 18: Console.WriteLine("6 AM"); break;
                    case 19: Console.WriteLine("7 AM"); break;
                    case 20: Console.WriteLine("8 AM"); break;
                    case 21: Console.WriteLine("9 AM"); break;
                    case 22: Console.WriteLine("10 AM"); break;
                    case 23: Console.WriteLine("11 AM"); break;
                    case 24: running = false; break;
                    case 25:
                        running = false;
                        Drip2(); // Переключение на 12-ти часовой формат
                        break;
                    default: Console.WriteLine("Ошибка. В сутках - 12 часов"); break;

                }
            }
        }

        static void Drip2()
        {
            bool running = true;

            while (running)
            {
                Console.WriteLine("1.Введите число от 0 до 23 что бы вывести время" +
                                  "\n2.Введите число 24 для смены формата на 12-ти часовой формат" +
                                  "\n3.Введите число 25 для выхода из программы");

                bool result = int.TryParse(Console.ReadLine(), out int hour24); // Булиана для проверки корректности входящего значения
                if (!result)
                {
                    // Выводим сообщение о некорректном символе и продолжаем цикл
                    Console.WriteLine("Некорректный символ");
                    continue;
                }

                switch (hour24)
                {
                    case 0: Console.WriteLine("12 часов ночи"); break;
                    case 1: Console.WriteLine("час ночи"); break;
                    case 2: Console.WriteLine("2 часа ночи"); break;
                    case 3: Console.WriteLine("3 часа ночи"); break;
                    case 4: Console.WriteLine("4 часа ночи"); break;
                    case 5: Console.WriteLine("5 часов ночи"); break;
                    case 6: Console.WriteLine("6 часов утра"); break;
                    case 7: Console.WriteLine("7 часов утра"); break;
                    case 8: Console.WriteLine("8 часов утра"); break;
                    case 9: Console.WriteLine("9 часов утра"); break;
                    case 10: Console.WriteLine("10 часов утра"); break;
                    case 11: Console.WriteLine("11 часов утра"); break;
                    case 12: Console.WriteLine("12 часов утра"); break;
                    case 13: Console.WriteLine("час дня"); break;
                    case 14: Console.WriteLine("2 часа дня"); break;
                    case 15: Console.WriteLine("3 часа дня"); break;
                    case 16: Console.WriteLine("4 часа дня"); break;
                    case 17: Console.WriteLine("5 часов дня"); break;
                    case 18: Console.WriteLine("6 часов вечера"); break;
                    case 19: Console.WriteLine("7 часов вечера"); break;
                    case 20: Console.WriteLine("8 часов вечера"); break;
                    case 21: Console.WriteLine("9 часов вечера"); break;
                    case 22: Console.WriteLine("10 часов вечера"); break;
                    case 23: Console.WriteLine("11 часов вечера"); break;
                    case 24:
                        running = false;
                        Drip1(); // Переключение на 12-ти часовой формат
                        break;
                    case 25:
                        running = false; // Выход из программы
                        break;
                    default:
                        Console.WriteLine("Ошибка. В сутках - 24 часа");
                        break;
                }
            }
        }

       
    }
}

using System;
using System.ComponentModel.Design;
using System.Xml.Linq;

namespace ConsoleApp1
{
    class Program
    {
        static void Main(string[] args)
        {
            Sbey();
        }
        static void Sbey()                                                 // Функция для получения месяца путём ввода числа
        {
            Console.WriteLine("Введите день недели", "(1-7):");
            bool result = int.TryParse(Console.ReadLine(), out int day); // Булиана для проверки корректности входящего значения
            if (!result)
            {                                                 // Выводим сообщение о некорректном символе, выходим из функции и заходим повторно 
                Console.WriteLine("Некорректный символ");
                Sbey();
            }

            switch (day)
            {
                case 1: Console.WriteLine("Понедельник - 2 пары программирования, 1 пара физры и экономики"); break;
                case 2 or 4:
                    int week;
                    do
                    {
                        Console.WriteLine("Какая это неделя? (1-2):");
                        bool result_2 = int.TryParse(Console.ReadLine(),out week);
                     
                        if (!result_2)
                        { 
                            Console.WriteLine("Не введено число 1-2."); 
                        }
                        else if (result_2 && (week == 1 || week == 2)) // Проверка на корректность ввода
                        {
                            break; // Выход из цикла, если введено корректное значение
                        }
                        else
                        {
                            Console.WriteLine("Неверное число недели.");
                        }
                    } while (true); // Цикл продолжается, пока не будет введено корректное значение

                    switch (week)
                    {
                        case 1:
                            if (day == 2) { Console.WriteLine("Вторник, 4 пары программирования"); }
                            else if (day == 4) { Console.WriteLine("Четверг, 3 пары программирования и физра"); }
                            break;
                        case 2:
                            if (day == 2) { Console.WriteLine("Вторник, 3 пары программирования"); }
                            else if (day == 4) { Console.WriteLine("Четверг, 3 пары программирования и алгебра"); }
                            break;
                    }
                    break;
                case 3: Console.WriteLine("Среда - 2 пары программирования 1 пара экономики"); break;
                case 5: Console.WriteLine("Пятница - 4 пары программирования"); break;
                case 6: Console.WriteLine("Суббота - Выходной"); break;
                case 7: Console.WriteLine("Воскресенье - Выходной"); break;
                default: Console.WriteLine("Неверное число"); break;
            }         
            Sbey(); // перевызов функции во избежание автоматического завершения 
        }
    }
}
