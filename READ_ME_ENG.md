This program is in the C # programming language,
produces finding the area of ​​a figure using a definite integral by the method of curvilinear trapezium,
where the limits of a definite integral, the entire quadratic function of the form t1 + t2 * x + t3 * x * x,
including the arithmetic signs "+" and "-" are entered by the user.
The user can also enter any incomplete quadratic function of the form t2 * x + t3 * x * x; t2 * x etc.
necessarily entering the place of the empty term of the equation "0". Amount of points,
into which the figure is divided for more accurate finding of the area is equal to 1000,
which is fully acceptable for this method.

The main module MetodKrivolineinihTrapecii contains the main function:
main - the task of entering the upper and lower limits of the user,
checking the upper and lower limits for compliance with the rule,
and also console output of the area already found.

Methods with which the main function works:
1) The function of the equation f (x) is responsible for calculating the result of the function of the equation,
taking into account the data entered by the user about the function, and the transfer of this result to the Trapezoidal method;
2) The function of finding the area Trapezoidal - finds the area of ​​the figure by the method of curvilinear trapezoids,
calculating the height of each point into which the figure is divided for calculation and 
summing up the calculated area of ​​each of these points.