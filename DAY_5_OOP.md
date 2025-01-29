Question:

Polymorphism
C++
Structure & Classes
medium
89.3% Success

8

0

Bookmark
Polymorphism
The term Polymorphism means the ability to take many forms. It occurs if there is a hierarchy of classes which are all related to each other by inheritance.
C++ polymorphism means that a call to a member function will cause a different function to be executed depending on the type of object that invokes the function.

The + operator in C++ is used to perform two specific functions. When it is used with numbers (integers and floating-point numbers), it performs addition.

int a = 5;
int b = 6;
int sum = a + b; // sum = 11
And when we use the + operator with strings, it performs string concatenation.

string firstName = "Samad ";
string lastName = "Sharma";
// name = "Samad Sharma"
string name = firstName + lastName;
In C++ polymorphism is mainly divided into two types:

Compile time Polymorphism
Runtime Polymorphism


Function Overloading

In C++, we can use two functions having the same name if they have different parameters (either types or number of arguments).

And, depending upon the number/type of arguments, different functions are called.

// C++ program to overload sum() function

#include <iostream>
using namespace std;

// Function with 2 int parameters
int sum(int num1, int num2) {
 return num1 + num2;
}

// Function with 2 double parameters
double sum(double num1, double num2) {
 return num1 + num2;
}

// Function with 3 int parameters
int sum(int num1, int num2, int num3) {
 return num1 + num2 + num3;
}

int main() {
 // Call function with 2 int parameters
 cout << "Sum 1 = " << sum(5, 6) << endl;

// Call function with 2 double parameters
 cout << "Sum 2 = " << sum(5.5, 6.6) << endl;

// Call function with 3 int parameters
 cout << "Sum 3 = " << sum(5, 6, 7) << endl;

return 0;
}
It’s a compile-time polymorphism because the compiler knows which function to execute before the program is compiled.

Operator Overloading

In C++, we can overload an operator as long as we are operating on user-defined types like objects or structures.
We cannot use operator overloading for basic types such as int, double, etc.

Operator overloading is basically function overloading, where different operator functions have the same symbol but different operands.
And, depending on the operands, different operator functions are executed.

Syntax

To overload an operator, we use a special operator function.

class className {
    ... .. ...
    public
        returnType operator symbol (arguments) {
            ... .. ...
        } 
    ... .. ...
};
returnType is the return type of the function.
operator is a keyword.
symbol is the operator we want to overload. Like: +, <, -, ++, etc.
arguments is the arguments passed to the function.
Since operator overloading allows us to change how operators work, we can redefine how the + operator works and use it to add the complex numbers of c1 and c2 by writing the following code:

#include<iostream> 
using namespace std; 
  
class Complex {
private: 
    int real, imag; 
public:
    Complex(int r = 0, int i =0)  {real = r;   imag = i;} 
      
    // This is automatically called when '+' is used with 
    // between two Complex objects 
    Complex operator + (Complex const &obj) { 
         Complex res; 
         res.real = real + obj.real; 
         res.imag = imag + obj.imag; 
         return res; 
    } 
    void print() { cout << real << " + i" << imag << endl; } 
}; 
  
int main() 
{ 
    Complex c1(10, 5), c2(2, 4); 
    Complex c3 = c1 + c2; // An example call to "operator+" 
    c3.print(); 
}
Try the following example in the editor below.

Your task is to create two functions with same name “compute” and return type int. One will take two integer parameters and return absolute difference between them. Other will take one integer parameter and return the square of that number.

Platform: InterviewBit (https://www.interviewbit.com/problems/polymorphism/)

Approach: Just implement the functions compute.

Code:

/*
#include<iostream>
using namespace std;
*/

// YOUR CODE GOES HERE

int compute(int x, int y){
    return abs(x-y);
}  
int compute(int x){
    return x*x;    
}  

/*
int main()  {
    int x,y;
    cin>>x>>y;
    cout<<compute(x,y)<<endl;
    int z;
    cin>>z;
    cout<<compute(z)<<endl;
    return 0;
}
*/
