Question:

Runtime Polymorphism (Virtual Functions)
C++
Structure & Classes
medium
81.7% Success

8

0

Bookmark
Function Overriding

In C++ inheritance, we can have the same function in the base class as well as its derived classes.

When we call the function using an object of the derived class, the function of the derived class is executed instead of the one in the base class.

So, different functions are executed depending on the object calling the function.

This is known as function overriding in C++. The function in derived class overrides the function in base class.

// C++ program to demonstrate function overriding

#include <iostream>
using namespace std;

class Base {
   public:
    void print() {
        cout << "Base Function" << endl;
    }
};

class Derived : public Base {
   public:
    void print() {
        cout << "Derived Function" << endl;
    }
};

int main() {
    Derived derived1;
    derived1.print();
    return 0;
}
// Output: Derived Function
Here, the same function print() is defined in both Base and Derived classes.
So, when we call print() from the Derived object derived1, the print() from Derived is executed by overriding the function in Base.

Virtual Functions

A virtual function is a member function which is declared in the base class using the keyword virtual and is re-defined (Overriden) by the derived class.
In C++ what this means is that if we call a member function then it could cause a different function to be executed instead depending on what type of object invoked it.

Let’s look at an example to understand it better.

// Without virtual function
#include <iostream>
using namespace std;

// Base class
class Shape {
   public:
      Shape(int l, int w){length = l; width=w;} //default constructor
      int get_Area(){cout << "This is call to parent class area"<<endl;}
  protected:
      int length,width;
};

// Derived class
class Square: public Shape {
   public:
      Square(int l=0, int w=0) : Shape(l,w) {} //declaring and initializing derived class constructor 
      int get_Area(){
        cout << "Square area: " << length*width << endl;
        return (length * width);  
      }
};
// Derived class
class Rectangle: public Shape {
   public:
      Rectangle(int l=0, int w=0) : Shape(l,w) {} //declaring and initializing derived class constructor 
      int get_Area(){ cout << "Rectangle area: " << length*width << endl;return (length * width); }
};

int main(void) {
   Shape *s;
   Square sq(5,5); //making object of child class Sqaure
   Rectangle rec(4,5); //making object of child class Rectangle
   
   s = &sq;
   s->get_Area();
   s= &rec;
   s->get_Area();
   return 0;
}
// Output
// This is call to parent class area
// This is call to parent class area
In the above function,

we store the address of each child class Rectangle and Square object in s and
then we call the get_Area() function on it,
ideally, it should have called the respective get_Area() functions of the child classes but
instead it calls the get_Area() defined in the base class.
This happens due static linkage which means the call to get_Area() is getting set only once by the compiler which is in the base class.
We can overcome static linkage​ problem by the use of virtual functions.
If we define a virtual function in the base class, with another version in a derived class, it will signal the compiler that we don’t want static linkage for this function.

Look at the modified code below:

#include <iostream>
using namespace std;

// Base class
class Shape {
   public:
      Shape(int l, int w){length = l; width=w;} //default constructor
      //changing get_Area() to virtual type function
      virtual int get_Area(){cout << "This is call to parent class area"<<endl;} 
  protected:
      int length,width;
};

// Derived class
class Square: public Shape {
   public:
      Square(int l=0, int w=0) : Shape(l,w) {} //declaring and initializing derived class constructor 
      int get_Area(){
        cout << "Square area: " << length*width << endl;
        return (length * width);  
      }
};
// Dreived class
class Rectangle: public Shape {
   public:
      Rectangle(int l=0, int w=0) : Shape(l,w) {} //declaring and initializing derived class constructor 
      int get_Area(){ cout << "Rectangle area: " << length*width << endl;return (length * width); }
};

int main(void) {
   Shape *s;
   Square sq(5,5); //making object of child class Sqaure
   Rectangle rec(4,5); //making object of child class Rectangle
   
   s = &sq;
   s->get_Area();
   s= &rec;
   s->get_Area();
   return 0;
}
// Output
// Square area: 25 
// Rectangle area: 20
Now when addresses of objects of Rectangle and Square​ classes are stored in *s the respective get_Area() function is called since this time, the compiler looked at the contents of the pointer rather than its type.

Try the following example in the editor below.

You will first build three classes:

Animal (parent class)
Dog (derived class)
Cat (derived class)
Dog and Cat class will inherit from Animal.

In the editor below you have to implement the following:

Animal class:
Has one protected variable for age of the mammal.
A constructor that takes the age of animal as input and sets it.
The function Eat() that displays "Animal eats food".
Function get_Age() which returns the age of the animal.
Dog class:
Inherits all the members from Animal class.
Implement all member functions of Animal class for Dog class.
Eat() should display "Dog eats meat".
get_Age() should return Dog’s age.
Cat class:
Inherits all the members from Animal class.
Implement all member functions of Animal class for Cat class.
Eat() should display "Cat eats meat".
get_Age() should return Cat’s age.
You are given main function displaying all the class functions and objects called and created.

Following should be the output after running the program:

Dog eats meat
Dog's age is: 8
Cat eats meat
Cat's age is 3

Platform: InterviewBit(https://www.interviewbit.com/problems/runtime-polymorphism-virtual-functions/)

Approach: Used the virtual functions(Eats(), get_Age()) in Animal class and override it in derived class of Dog and Cat.

Code:

/*
#include<iostream>
using namespace std;
*/

// Your code goes here
class Animal{
    protected:
    int age;
    public:
    Animal(int age){
        this->age = age;
    }
    virtual void Eat(){
        cout<<"Animal eats food\n";
    }
    virtual int get_Age(){
        return age;
    }
};

class Dog : public Animal{
    protected:
    int age;
    public:   
    Dog(int age) : Animal(age){}    
    void Eat() override {
        cout<<"Dog eats meat\n";
    }
};

class Cat : public Animal{
    public:
    Cat(int age) : Animal(age) {}
    void Eat() override {
        cout<<"Cat eats meat\n";
    }
};

/*
int main()  {
   Animal *a;
   Dog dg(8); //making object of child class Dog
   Cat ct(3); //making object of child class Cat
   
   a = &dg;
   a->Eat();
   cout << "Dog's age is: "<<a->get_Age()<<endl;
   a= &ct;
   a->Eat();
   cout << "Cat's age is: "<<a->get_Age()<<endl;
   return 0;
}
*/
