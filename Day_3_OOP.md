Question:

Provides a way to create a new class from an existing class. 
New class is a specialized version of the existing class.

Base Class(or Parent): inherited by child class.
Derived Class(or child): inherits from base class.
class Student{ //base class
 //body
}; 

class UnderGrad : public Student{  //derived class
  //body
};
Inheritance establishes an “is a” relationship between classes.

An object of the derived class “is a” object of the base class. For example:

An UnderGrad is Student.
A derived object has all​ characteristics of the base class.

An object of child class has:

All members defined in the child class.
All ​members declared in the parent class.
An object of child class can use:

All public members defined in the child class.
All public members defined in the parent class.
Protected Members

protected member access specification: similar to private, but accessible by objects of derived class.
Class Access Specifiers

public: the object of the derived class can be treated as an object of the base class.
protected: more restrictive than public, but allows derived classes to know details of parents.
private: prevents objects of the derived class to be treated as objects of base class.
#include <iostream>
using namespace std;

// Base class
class Shape {
   public:
      Shape(){length = 0; width = 0;} //default constructor
      void setlength(int l, int w) {length = l; width = w;}
  protected:
      int length, width;
};

// Derived class
class Square: public Shape {
   public:
      Square() : Shape() {} //declaring and initializing derived class constructor 
      int get_Area(){ return (length * width); }
};

int main(void) {
   Square sq; //making object of child class Square
   sq.setlength(5, 5); //setting length equal to 5
   // Print the area of the object.
   cout << "Total area of square is: " << sq.get_Area() << endl;

   return 0;
}
As you can see in the example above,

The shape class is the parent class whereas the Square class is the child class derived from it.
In our child class Square, we use members from the parent class such as
the protected length and width variable which gets initialized to zero in the default constructor.
Length and width also gets used in child class function get_Area to compute the area of the square.
In main the setlength function which is a public member function of the parent class is accessible to the child class object sq
The dot operator is used to access setlength in the main.
Try the following example in the editor below.

With reference to above example, create a derived class Rectangle inherited from class Shape, your task is to create a public function in it named get_Perimeter which return the perimeter of rectange.

Platform: Interview Bit (https://www.interviewbit.com/problems/inheritance/)

Approach : Just implement the Rectangle class by inheriting Shape class.

Code:

/*
#include <iostream>
using namespace std;

// Base class
class Shape {
   public:
      Shape(){length = 0; width = 0;} //default constructor
      void setlength(int l, int w) {length = l; width = w;}
  protected:
      int length, width;
};

// Derived class
class Square: public Shape {
   public:
      Square() : Shape() {} //declaring and initializing derived class constructor 
      int get_Area(){ return (length * width); }
};
*/

// Create class Rectangle

class Rectangle : public Shape{
    public:
    Rectangle() : Shape() {}
    int get_Perimeter(){
        return 2 * (length + width);
    }
};


/*
int main(void) {
   Square sq; //making object of child class Square
   sq.setlength(5, 5); //setting length equal to 5
   // Print the area of the object.
   cout << "Total area of square is: " << sq.get_Area() << endl;
   Rectangle rc;
   rc.setlength(10, 5);
   // Print the perimeter of the object.
   cout << "Total perimeter of rectangle is: " << rc.get_Perimeter() << endl;
   return 0;
}
*/
