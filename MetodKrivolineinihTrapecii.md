using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace MKT
{
    class Program
    {   // члены квадратного уравнения, вводятся пользователем 1 раз
        public static double t1;
        public static double t2;
        public static double t3;
        // знаки между членами квадратного уравнения, вводятся пользователем 1 раз, истина + ложь -
        public static bool z1;
        public static bool z2;
        public static void Main(string[] args)
        {
            int n = 1000; // число точек, в которых вычисляется значение подынтегральной функции методом криволинейных трапеций
            double result, a, b; 
            Console.WriteLine("Введите нижний предел интеграла");
            a = double.Parse(Console.ReadLine());
            Console.WriteLine("Введите верхний предел интеграла");
            b = double.Parse(Console.ReadLine());
            if (a > b)
            {
                Console.WriteLine("Должно быть a < b");
                Console.ReadKey();
                return; // окончание работы программы из-за несоответствия правилу
            }
            else
            {
                result = Trapezoidal(a, b, n); // вывод просчитанного результата из метода Trapezoidal 
                Console.WriteLine("Результат = " + result.ToString()); // вывод результата
                Console.ReadKey();
                return;
            }
        }

        public static double f(double x) // метод нахождения функции от введенного пользователем квадратного уравнения
        { // данный метод используется в цикле метода Trapezoidal, поэтому чтобы цикл не прерывать, в него отзеркаливаются уже выбранные пользователем параметры, которые до введенния пользователем = 0
            if (t1 != 0 && t2 != 0 && t3 != 0) 
            {
                if (z1 == true && z2 == true)
                {
                    return t1 + t2 * x + t3 * x * x; // передача функции данного метода методу Trapezoidal
                }
                if (z1 == false && z2 == false)
                {
                    return t1 - t2 * x - t3 * x * x;
                }
                if (z1 == true && z2 == false)
                {
                    return t1 + t2 * x - t3 * x * x;
                }
                if (z1 == false && z2 == true)
                {
                    return t1 - t2 * x + t3 * x * x;
                }
            }
            // когда квадратное уравнение не полное и какие-то члены уравнения = 0, сделано чтоб меньше нагружать ЦП лишними вычислениями с 0 членами уравнения
            if (t1 != 0 && t2 != 0) 
                {
                    if (z1 == true)
                    {
                        return t1 + t2 * x;
                    }
                    if (z1 == false)
                    {
                        return t1 - t2 * x;
                    }
                }
                if (t2 != 0 && t3 != 0)
                {
                    if (z2 == true)
                    {
                        return t2 * x + t3 * x * x;
                    }
                    if (z2 == false)
                    {
                        return t2 * x - t3 * x * x;
                    }
                }
               if (t1 != 0 && t3 != 0)
                {
                    if (z1 == true)
                    {
                        return t1 + t3 * x * x;
                    }
                    if (z1 == false)
                    {
                        return t1 - t3 * x * x;
                    }
                }
                if (t1 != 0 && t2 == 0 && t3 == 0)
                 {
                     return t1;
                 }
                 if (t1 == 0 && t2 != 0 && t3 == 0)
                 {
                     return t2;
                 }
                 if (t1 == 0 && t2 == 0 && t3 != 0)
                 {
                     return t3;
                 }  
               Console.WriteLine("Введите свободный член квадратного уравнения подинтегральной функции t1 вида t1+t2*х-t3*х*х или 0 при его отсутствии");
             t1 = double.Parse(Console.ReadLine());
             Console.WriteLine("Введите зависимое 1-го уровня квадратного уравнения подинтегральной функции t2 вида t1+t2*х-t3*х*х или 0 при его отсутствии");
              t2 = double.Parse(Console.ReadLine());
              Console.WriteLine("Введите зависимое 2-го уровня квадратного уравнения подинтегральной функции t3 вида t1+t2*х-t3*х*х или 0 при его отсутствии");
             t3 = double.Parse(Console.ReadLine());
             if (t1 != 0 && t2 != 0 && t3 != 0) // ввод знаков только после ввода всех членов уравнения
            {
                Console.WriteLine("Введите знак между t1 и t2 true = + false = - "); // знак вводится только true или false
                z1 = bool.Parse(Console.ReadLine());
                Console.WriteLine("Введите знак между t2 и t3 true = + false = - ");
                z2 = bool.Parse(Console.ReadLine());
                if (z1 == true && z2 == true)
                {
                    return t1 + t2 * x + t3 * x * x;
                }
                if (z1 == false && z2 == false)
                {
                    return t1 - t2 * x - t3 * x * x;
                }
                if (z1 == true && z2 == false)
                {
                    return t1 + t2 * x - t3 * x * x;
                }
                else
                {
                    return t1 - t2 * x + t3 * x * x;
                }
            }
            else
             {
                 if (t1 != 0 && t2 != 0)
                 {
                     Console.WriteLine("Введите знак между t1 и t2 true = + false = - "); // знак вводится только true или false
                     z1 = bool.Parse(Console.ReadLine());
                     if (z1 == true)
                     {
                         return t1 + t2 * x;
                     }
                     if (z1 == false)
                     {
                         return t1 - t2 * x;
                     }
                 }
                 if (t2 != 0 && t3 != 0)
                 {
                     Console.WriteLine("Введите знак между t2 и t3 true = + false = - "); // знак вводится только true или false
                     z2 = bool.Parse(Console.ReadLine());
                     if (z2 == true)
                     {
                         return t2 * x + t3 * x * x;
                     }
                     if (z2 == false)
                     {
                         return t2 * x - t3 * x * x;
                     }
                 }
                 if (t1 != 0 && t3 != 0)
                 {
                     Console.WriteLine("Введите знак между t1 и t3 true = + false = - "); // знак вводится только true или false
                     z1 = bool.Parse(Console.ReadLine());
                      if (z1 == true)
                     {
                         return t1 + t3 * x * x;
                     }
                     if (z1 == false)
                     {
                         return t1 - t3 * x * x;
                     }
                 }
                 if (t1 != 0 && t2 == 0 && t3 == 0)
                 {
                     return t1;
                 }
                 if (t1 == 0 && t2 != 0 && t3 == 0)
                 {
                     return t2;
                 }
                 if (t1 == 0 && t2 == 0 && t3 != 0)
                 {
                     return t3;
                 }
                 else
                 {
                     Console.WriteLine("Вы не ввели уравнение");
                     Console.ReadKey();
                     return 0;
                 }
            }
        }

        public static double Trapezoidal(double a, double b, int n) // находит площадь фигуры методом криволинейных трапеций
        { 
            double sum = 0.0;
            double h = (b - a) / n; // высота одной точки для вычисления площади фигуры    
            for (int i = 0; i < n; i++) // нахождение площади фигуры в каждой точке и суммирование общего результата со всех точек
            {
                sum += Math.Abs(0.5 * h * (f(a + i * h) + f(a + (i + 1) * h)));  // модуль числа результата нахождения площади так как она всегда положительная
            }
            return sum; 
        }
    }
}