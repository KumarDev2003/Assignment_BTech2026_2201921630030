Question:

Classes and Objects
C++
Structure & Classes
medium
83.3% Success

9

6

Bookmark
Classes are the building blocks of programs built using the object-oriented methodology. Such programs consist of independent, self-managing modules and their interactions. An object is an instance of such module, and a class is its definition.

class className 
{
  variable var1;         // variables names can be of type string, int, float
  variable var2;         
};                       // class body always terminates with ';' 
A Keyword class is used with every declaration of class followed by the name of the class. You can use any className as you want.

Example

class Person
{
public:
    char name[25];
    string gender;
    int age;
    int weight;
    bool healthy;
};

int main(){
  Person personObj;     // creating an object of Person class called personObj
  //using the dot operator to access members of a class
  personObj.gender;  //using object personObj to access certain accessible variables of the class
}
Explanation

A person has several member variables listed such a:

name,
the gender of the person,
the age of the person,
its weight,
whether it is healthy or not.
These variables are called properties declared inside the class.

An instance of a person, say, a person named Robin, would be an object. So would a person named Rahul. Hence, you can have multiple instances of a class, just like there can be multiple person.

Properties are like “inner variables” of each object made of type Person. We used the dot operator to access members of a class object.

Private Members

As you can see above, we have used the word public before declaring the class members. The reason being:

C++ restricts the program from directly referencing the member variables.
By default, all members declared inside a class are considered private. Which means:

they can only be referenced within the definitions of member functions
If a program tried to access private variables directly it will get a compiler error.
Note: Private members can be variables or functions.

Public Members 

The keyword public identifies members of a class that can be accessed from outside of the class.

Members that follow the keyword public are public members of the class.

Definig Member Functions
Member functions are declared in the class declaration. Member function definitions identify the class in which the function is a member.

class DayOfYear {
public:
    void output(); //member function
    int month;
    int day;
};

void DayOfYear::output(){   //indicates function output is member of DayOfYear class
  cout << "Month =  " << month <<endl;
  cout << "Day =  " << day <<endl;
}
Setters and Getters
As we discussed above, private member variables cannot be accessed directly in any other function.

In order to access or change their values, we need to define public member functions. These functions can be used to set the values of the private variables as well as to get their values since being private these members cannot be accessed directly.

//Class with Private Members 
//Program to demonstrate the class DayOfYear.
#include <iostream>
using namespace std;

class DayOfYear
{
public:
      int myVar;
    void output( );

    void set(int new_month, int new_day);
    //Precondition: new_month and new_day form a possible date.
    //Postcondition: The date is reset according to the arguments.

    int get_month( );
    //Returns the month, 1 for January, 2 for February, etc.

    int get_day( );
    //Returns the day of the mont
private:  //private variables not accessible directly in main
    void check_date( );  //checks the date
    int month;    
    int day;
};

int main( )
{
    DayOfYear today, birthday; //making two objects of DayOfYear class
    //setting today object's month and day
    today.set(11,23); 
    cout << "Today's date is ";
    today.output( );    //calling output to display today object's month and day
    
    //setting birthday object's month and day
    birthday.set(3, 21);  //try setting these values same as one passed for today. 
                            //also try passing invalid values here and then run code
    cout << "Birthday date is ";
    birthday.output( );  //calling output to display birthday object's month and day

    if (today.get_month() == birthday.get_month() //if condition to check if today object's month/day 
       && today.get_day() == birthday.get_day() ) //equals birthday object's month/day
        cout << "Happy Birthday!\n";    //if matched it's your birthday
    else
        cout << "It's not your birthday\n";  //if dates don't match it's not your birthday
    return 0;
}

//function definitions

void DayOfYear::output()
 {
  //displays the set month and day
  
    cout << "month = " << month
         << ", day = " << day << endl;
  
}

void DayOfYear::set(int new_month, int new_day) //setting
{
    month = new_month; //sets private variable month equal to argument new_month
    day = new_day;  //sets private variable day equal to argument new_day
    check_date(); //calling check_date to see if the month and date entered are valid
}

void DayOfYear::check_date( )
{
  //checking to see if month and date values are valid
    if ((month < 1) || (month > 12) || (day < 1) || (day > 31)) 
    {
        cout << "Illegal date. Aborting program.\n";
        exit(1);  //program exits if values are invalid
    }
}

int DayOfYear::get_month( )
{
    return month;    //retuns the private variable month
}

int DayOfYear::get_day( )
{
    return day;    //returns the private variable day
}
Explanation

First we make a class named DayOfYear and declare the public and private variables.
Public variables include:
Variable myVar
The functions output, set, get_month, get_day
Private variables include:
Variables month, day
Fucntions check_date
Let’s take a look at all the functions one by one.

 

check_date()

It checks whether the values of month and day are valid, if they are not, it gives an error and aborts the program.
set(int new_month, int new_day)

In the example before when member variables were public, we set the date and month of an object by directly accessing these member variables in our main function using the dot operator.
However, we can’t set private variables directly in the main hence we use the public function set which can access these private variables. It takes the input arguments new_month and new_day and sets the values of month and day equal to them.
It then calls the check_date() function to see if both values are valid.
get_month()

Returns the value of month as it is a private can’t be accessed directly in the main function.
get_day()

Returns the value of day as it is a private can’t be accessed directly in the main function.
output()

Displays the month and day.
main()

Declares two objects today and birthday for class DayofYear.
Calls set function to update the values of day and month for both the objects.
Calls the output function to display today date and birthday date.
Lastly, it checks whether today date matches birthday date, if it does, it means it’s their birthday.
Try the following example in the editor below.

We have a class defined for Student. Create a function set_variable which takes three parameters name(string), age(int), rollno(int) and assign values to the member variables. Also, create a function print_variable which prints name, age, rollno each in new line.

Platform: InterviewBit (https://www.interviewbit.com/problems/classes-and-objects-cpp/)

Approach: Assigned the variable using (this->) pointer and implemented the print fucntion.

Code:

/*
#include<iostream>
#include<bits/stdc++.h>
using namespace std;
*/

class Student{
    string name;
    int age;
    int rollno;
public:
    // Create funtions here with the name given
    void set_variable(string name, int age, int rollno){
        this->name = name;
        this->age = age;
        this->rollno = rollno;
    }
    void print_variable(){
        cout<<name<<endl;
        cout<<age<<endl;
        cout<<rollno<<endl;
    }
};



/*
int main()  {
    Student obj1;
    obj1.set_variable("Robin", 15, 10);
    Student obj2;
    obj2.set_variable("Rahul", 20, 14);
    obj1.print_variable();
    obj2.print_variable();
    return 0;
}
*/

