# C# - linq library

```csharp

using System;
using System.Collections.Generic;
using System.Linq;

// Создание класса Question
class Question
{
    public int id { get; set; }
    public string? name { get; set; }
}

class Program
{
    static void Main(string[] args)
    {
        // Создание списка tVopros
        List<Question> tVopros = new List<Question> {
            new Question { id = 1, name = "Вопрос 1" },
            new Question { id = 2, name = "Вопрос 2" },
            new Question { id = 3, name = "Вопрос 1" },
            new Question { id = 4, name = "Вопрос 3" }
        };

        // Задание 1.1: поиск единственного элемента
        Question? question = tVopros.Where(x => x.id == 1).FirstOrDefault();
        Console.WriteLine($"Единственный элемент с id = 1: {question?.name ?? "Нет элемента"}");

        // Задание 1.2: поиск списка элементов
        List<Question> newQuestions = tVopros.Where(x => x.name == "Вопрос 1").ToList();
        Console.WriteLine($"Список вопросов с именем 'Вопрос 1': {string.Join(", ", newQuestions.Select(x => x.id))}");

        // Задание 2: получение количества элементов по условию
        int count = tVopros.Count(x => x.id == 1);
        Console.WriteLine($"Количество элементов с id = 1: {count}");

        // Задание 3.1: выборка нужных полей
        var selectedQuestions = tVopros.Select(x => new { x.id, x.name });
        Console.WriteLine("Выбранные поля:");
        foreach (var q in selectedQuestions)
        {
            Console.WriteLine($"id = {q.id}, name = {q.name}");
        }

        // Задание 3.2: сортировка
        var sortedQuestions = tVopros.OrderByDescending(x => x.id);
        Console.WriteLine("Отсортированные элементы (по убыванию): ");
        foreach (var q in sortedQuestions)
        {
            Console.WriteLine($"id = {q.id}, name = {q.name}");
        }

        // Задание 3.3: проверка наличия элементов
        bool anyQuestions = tVopros.Any(x => x.name == "Вопрос 2");
        Console.WriteLine($"Есть ли вопросы с именем 'Вопрос 2': {anyQuestions}");

        // Задание 3.4: сумма значений
        int sumIds = tVopros.Sum(x => x.id);
        Console.WriteLine($"Сумма значений поля 'id': {sumIds}");

        // Задание 3.5: минимальное значение
        int minId = tVopros.Min(x => x.id);
        Console.WriteLine($"Минимальное значение поля 'id': {minId}");

        // Задание 3.6: максимальное значение
        int maxId = tVopros.Max(x => x.id);
        Console.WriteLine($"Максимальное значение поля 'id': {maxId}");

        // Задание 3.7: выборка определенного количества элементов
        var firstTwoQuestions = tVopros.Take(2);
        Console.WriteLine("Первые два элемента:");
        foreach (var q in firstTwoQuestions)
        {
            Console.WriteLine($"id = {q.id}, name");
        };

        // Задание 3.8: пропуск определенного количества элементов
        var skippedQuestions = tVopros.Skip(2);
        Console.WriteLine("Пропущенные два элемента:");
        foreach (var q in skippedQuestions)
        {
            Console.WriteLine($"id = {q.id}, name = {q.name}");
        }

        // Задание 3.9: последний элемент
        Question lastQuestion = tVopros.Last();
        Console.WriteLine($"Последний элемент: id = {lastQuestion.id}, name = {lastQuestion.name}");

        // Задание 3.10: последний элемент по условию (или значение по умолчанию)
        Question? lastOrDefaultQuestion = tVopros.LastOrDefault(x => x.name == "Вопрос 2");
        Console.WriteLine($"Последний элемент с именем 'Вопрос 2' (или значение по умолчанию): {lastOrDefaultQuestion?.id ?? -1}");

        // Задание 3.11: единственный элемент по условию (или значение по умолчанию)
        Question? singleOrDefaultQuestion = tVopros.SingleOrDefault(x => x.id == 2);
        Console.WriteLine($"Единственный элемент с id = 2 (или значение по умолчанию): {singleOrDefaultQuestion?.name ?? "Нет элемента"}");
    }
}


```
