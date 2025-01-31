Question:

Structures
C++
Structure & Classes
medium
85.1% Success

8

0

Bookmark
Structure is a collection of variables of different data types under a single name. It is similar to a class in that, both holds a collecion of data of different data types.

For example: You want to store some information about a person: his/her name, citizenship number and salary. You can easily create different variables name, citNo, salary to store these information separately.

However, in the future, you would want to store information about multiple persons. Now, you’d need to create different variables for each information per person: name1, citNo1, salary1, name2, citNo2, salary2

You can easily visualize how big and messy the code would look. Also, since no relation between the variables (information) would exist, it’s going to be a daunting task.

A better approach will be to have a collection of all related information under a single name Person, and use it for every person. Now, the code looks much cleaner, readable and efficient as well.

This collection of all related information under a single name Person is a structure.

Declaration
The struct keyword defines a structure type followed by an identifier (name of the structure).

Then inside the curly braces, you can declare one or more members (declare variables inside curly braces) of that structure.

 For example:

struct Person
{
    char name[50];
    int age;
    float salary;
};
Here a structure person is defined which has three members: name, age and salary.
When a structure is created, no memory is allocated.
The structure definition is only the blueprint for the creating of variables. You can imagine it as a datatype.

Note: Remember to end the declaration with a semicolon (;)

Definition

Once you declare a structure person as above. You can define a structure variable as:

Person x;
Here, a structure variable bill is defined which is of type structure Person.

When structure variable is defined, only then the required memory is allocated by the compiler.

Access Members
The members of structure variable is accessed using a dot (.) operator.

Suppose, you want to access age of structure variable x and assign it 30 to it. You can perform this task by using following code below:

x.age = 30;
Try the following example in the editor below.

Create a structure named ‘student’, containing three members: name (string), rollno(int) and marks(int).

Set name to "Robin"
Set rollno to 11
Set marks to 86
Note: Variable name for structure ‘student’ should be s1.

Platform: InterviewBit(https://www.interviewbit.com/problems/structures/)

Approach: Assign the value by creating the object.

Code:

/*
#include<iostream>
#include<string>
using namespace std;
*/


// Create Structure named 'student'
struct Person{
    string name;
    int rollno;
    int marks;
};

int main()  {
    // Your code goes here
    Person s1;
    s1.name = "Robin";
    s1.rollno = 11;
    s1.marks = 86;
    // Don't change the below code
    cout<<s1.name<<endl;
    cout<<s1.rollno<<endl;
    cout<<s1.marks<<endl;
    return 0;
}
