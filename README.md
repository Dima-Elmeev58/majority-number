# majority-number
class Program
{
    static void Main(string[] args)
    {
        int length = 10000; // Задаем длину массива - константу
        Random random = new Random(); // Создаем объект для генерации рандомных чисел
        int[] mass = new int[length]; // Создаем массив элементов для проверки наличия мажоритарного числа
        
        for (int i = 0; i < length; i++) // Перебор элементов массива
        {
            mass[i] = random.Next(0, 101); // Заполняем массив элементами от 0 до 100
        }
        
        int majority = FindMajorityElement(mass); // Вызываем метод для поиска мажоритарного числа
        
        if (majority != -1) // Проверяем, соответствует ли элемент параметрам мажоритарного числа
        {
            Console.WriteLine($"Мажоритарный элемент в данном массиве - {majority}");
        }
        else
        {
            Console.WriteLine("В данном массиве отсутствует мажоритарное число");
        }
    }

    static int FindMajorityElement(int[] nums) // Метод для поиска мажоритарного числа
    {
        int candidate = 0; // Задаем переменную для поиска кандидата
        int count = 0; // Счетчик для проверки числа
        
        foreach (var num in nums) // Перебор элементов массива
        {
            if (count == 0) // Если счетчик равен нулю
            {
                candidate = num; // Присваиваем кандидату значение элемента
                count = 1; // Увеличиваем счетчик
            }
            else if (candidate == num) // Если элемент равен кандидату
            {
                count++; // Увеличиваем счетчик
            }
            else // Если элемент не равен кандидату
            {
                count--; // Уменьшаем счетчик
            }
        }
        
        count = 0; // Установка счетчика в 0
        foreach (var num in nums) // Снова перебираем все элементы массива
        {
            if (candidate == num) // Если элемент равен кандидату
            {
                count++; // Увеличиваем счетчик
            }
        }
        
        if (count > nums.Length / 2) // Проверяем больше ли половины длины массива количество совпадений
        {
            return candidate; // Возвращаем кандидата
        }
        else 
        {
            return -1; // Если нет, возвращаем -1
        }
    }
}
