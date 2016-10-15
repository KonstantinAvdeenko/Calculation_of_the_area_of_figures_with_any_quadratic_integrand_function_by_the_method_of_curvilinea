﻿Данная программа на языке программирования C#, 
производит нахождение площади фигуры при помощи определенного интеграла методом криволинейных трапеций, 
где пределы определенного интеграла, всю квадратичную функцию вида t1 + t2 * x + t3 * x * x, 
включая арифметические знаки «+» и «-» вводит пользователь. 
Пользователь может также вводить любую неполную квадратичную функцию вида t2 * x + t3 * x * x;  t2 * x  и т.д.,  
обязательно введя на место пустого члена уравнения «0». Количество точек, 
на которые разбивается фигура для более точного нахождения площади равна 1000, 
что полностью приемлемо для данного метода.

Основной модуль MetodKrivolineinihTrapecii содержит основную функцию: 
main –выполняющую задачу ввода верхних и нижних пределов пользователя, 
проверку верхнего и нижнего пределов на соответствие правилу, 
а также консольного вывода уже найденной площади.

Методы с которыми работает основная функция:
1) Функция от уравнения f(x) – отвечает за расчет результата функции уравнения, 
с учетом введенных пользователем данных о функции, и передачу этого результата методу Trapezoidal;
2) Функция нахождения площади Trapezoidal – находит площадь фигуры методом криволинейных трапеций, 
рассчитывая высоту каждой точки, на которые делится фигура для расчета и суммируя рассчитанную площадь каждой этой точки.