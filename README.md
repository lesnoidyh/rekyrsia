# rekyrsia
{
    static class Program
    {
        public static void Main (string [] args)
        {
            Console.Clear();
            string stringLoad = "Введите номер задачи (от 1 до 3) => ";
            System.Console.Write(stringLoad);
            Tasks(NumberInTerminal(3,stringLoad,1));
        }
        static void Tasks(int num)
        {
            switch (num)
            {
                case 1:
                {
                    System.Console.WriteLine("Задача 1: Задайте значения M и N. Напишите программу, которая выведет ");
                    System.Console.WriteLine("все натуральные числа в промежутке от M до N. Использовать рекурсию, не использовать циклы.");
                    string firstText = "Введите значение М => ";
                    System.Console.Write(firstText);
                    int firstNumber = NumberInTerminal(0xFFFFFF,firstText,1);
                    string secondText ="Введите значение N => ";
                    System.Console.Write(secondText);
                    int secondNumber = NumberInTerminal(0xFFFFFF,secondText,1);
                    System.Console.WriteLine($"Числа от {firstNumber} до {secondNumber} => {ShowDigit(firstNumber,secondNumber)}");
                    break;
                }
                case 2:
                {
                    System.Console.WriteLine("Задача 2: Напишите программу вычисления функции Аккермана с помощью рекурсии.");
                    System.Console.WriteLine("Даны два неотрицательных числа m и n.");
                    string firstText = "Введите значение m => ";
                    System.Console.Write(firstText);
                    int firstNumber = NumberInTerminal(0xFFFFFF,firstText,0);
                    string secondText ="Введите значение n => ";
                    System.Console.Write(secondText);
                    int secondNumber = NumberInTerminal(0xFFFFFF,secondText,0);
                    System.Console.WriteLine($"Значение по фукнкции Аккермана ({firstNumber},{secondNumber}) = {Ack(firstNumber,secondNumber)}");
                    break;
                }
                case 3:
                {
                    System.Console.WriteLine("Задача 3: Задайте произвольный массив. Выведете его элементы,");
                    System.Console.WriteLine("начиная с конца. Использовать рекурсию, не использовать циклы.");
                    int [] array = CreateArray(10,10,0);
                    System.Console.WriteLine($"Произвольный массив => [{PrintArray(array)}]");
                    System.Console.WriteLine($"Перевернутый массив => [{PrintArray(ArraySwap(array,array.Length-1))}]");
                    break;
                }
            }
        }
        public static int [] CreateArray (int size, int max, int min){
            int [] array  = new int[size];
            Random rand = new();
            for (int i = 0; i < size; i++)
            {
                array [i] = rand.Next(min,max+1);
            }
            return array;
        }
        public static string PrintArray(int [] array)
        {
            return string.Join(", ",array);
        }
        public static int [] ArraySwap(int [] array,int index)
        {

            if (index <= 0)
            {
                return array;
            }
            int temp = array[index];
            array[index] = array[array.Length - index-1];
            array[array.Length - index-1] = temp;
            return ArraySwap(array,index -= 2);
        }
        public static int Ack(int m, int n)
        {
            if (m == 0) 
            {
                return n + 1;
            }
            else
            {
                if (n == 0) 
                {
                    return Ack(m - 1, 1);
                }
                else
                {
                    return Ack(m - 1, Ack(m, n - 1));
                } 
            }
        }
        public static string ShowDigit(int firstDigit,int secondDigit)
        {
            if (firstDigit > secondDigit)
            {
                return "";
            }
            return $"{firstDigit} " + ShowDigit(firstDigit+1,secondDigit);
        }
        /*Функция ввода чисел в терминале*/
        public static int NumberInTerminal(int numberDigits, string repeatString, int minValueSet)
        {
            string ? numString = Console.ReadLine();
            int numInt = 0;
            while ((!Int32.TryParse(numString,out numInt)) 
                    || !(numInt >= minValueSet) 
                    || !(numInt <= numberDigits)
                  )
            {
                System.Console.WriteLine("Ошибка ввода, повторите");
                System.Console.Write(repeatString);
                numString = Console.ReadLine(); 
            }
            return numInt;
        }

        public static void PrintArray(char [,] array)
        {
            int rows = array.GetLength(0);
            int cols = array.GetLength(1);
            string output = "";
            for (int i = 0; i < rows; i++)
            {
                for (int j = 0; j < cols; j++)
                {
                    output += array[i,j] + " ";
                }
                System.Console.WriteLine($"[ {output}]");
                output = "";
            }
        }
    }
}
