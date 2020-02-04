# What is a structure? 
A structure is a collection of variables of different data types.

a struct (or structure) is a collection of variables (can be of different types) under a single name

```
Syntax of struct
struct structureName 
{
    dataType member1;
    dataType member2;
    ...
};
```

Here is an example:
```c
struct Person
{
    char name[50];
    int emNo;
    float salary;
};
```

Here, a derived type struct Person is defined. Now, you can create variables of this type.

Create struct variables
When a struct type is declared, no storage or memory is allocated. 
To allocate memory of a given structure type and work with it, we need to create variables.

Here's how we create structure variables:
```c
struct Person
{
    char name[50];
    int emNo;
    float salary;
};

int main()
{
    struct Person person1, person2, p[20];
    return 0;
}
```
Another way of creating a struct variable is:
```c
struct Person
{
    char name[50];
    int emNo;
    float salary;
} person1, person2, p[20];
```
In both cases, two variables person1, person2, and an array variable p having 20 elements of type struct Person are created.

## Access members of a structure
There are two types of operators used for accessing members of a structure.
```
. - Member operator
-> - Structure pointer operator (will be discussed in the next tutorial)
```
Suppose, you want to access the salary of person2. Here's how you can do it.
```
person2.salary
```
### Example: Add two distances
```c
// Program to add two distances (feet-inch)
#include <stdio.h>
struct Distance
{
    int feet;
    float inch;
} dist1, dist2, sum;
int main()
{
    printf("1st distance\n");
    printf("Enter feet: ");
    scanf("%d", &dist1.feet);
    printf("Enter inch: ");
    scanf("%f", &dist1.inch);
    printf("2nd distance\n");
    printf("Enter feet: ");
    scanf("%d", &dist2.feet);
    printf("Enter inch: ");
    scanf("%f", &dist2.inch);
    // adding feet
    sum.feet = dist1.feet + dist2.feet;
    // adding inches
    sum.inch = dist1.inch + dist2.inch;
    // changing to feet if inch is greater than 12
    while (sum.inch >= 12) 
    {
        ++sum.feet;
        sum.inch = sum.inch - 12;
    }
    printf("Sum of distances = %d\'-%.1f\"", sum.feet, sum.inch);
    return 0;
}
```
### Output
```
1st distance
Enter feet: 12
Enter inch: 7.9
2nd distance
Enter feet: 2
Enter inch: 9.8
Sum of distances = 15'-5.7"
```
## How to declare structure variables?
A structure variable can either be declared with structure declaration or as a separate declaration like basic types.
```c
// A variable declaration with structure declaration. 
struct Point 
{ 
   int x, y; 
} p1;  // The variable p1 is declared with 'Point' 
  
  
// A variable declaration like basic data types 
struct Point 
{ 
   int x, y; 
};  
  
int main() 
{ 
   struct Point p1;  // The variable p1 is declared like a normal variable 
}
```
## How to initialize structure members?
Structure members cannot be initialized with declaration. For example the following C program fails in compilation.
```c
struct Point 
{ 
   int x = 0;  // COMPILER ERROR:  cannot initialize members here 
   int y = 0;  // COMPILER ERROR:  cannot initialize members here 
};  
```

## Example of Nested Structure in C Programming
Lets say we have two structure like this:
Structure 1: stu_address
```c
struct stu_address
{
     int street;
     char *state;
     char *city;
     char *country;
}
```
Structure 2: stu_data
```c
struct stu_data
{
    int stu_id;
    int stu_age;
    char *stu_name;
    struct stu_address stuAddress;
}
```
As you can see here that I have nested a structure inside another structure.

Assignment for struct inside struct (Nested struct)
Lets take the example of the two structure that we seen above to understand the logic
```c
struct  stu_data  mydata;
mydata.stu_id = 1001;
mydata.stu_age = 30;
mydata.stuAddress.state = "UP"; //Nested struct assignment
..
```
How to access nested structure members?
Using chain of “.” operator.
Suppose you want to display the city alone from nested struct –
```c
printf("%s",  mydata.stuAddress.city);
```
## Use of typedef in Structure
typedef makes the code short and improves readability. In the above discussion we have seen that while using structs every time we have to use the lengthy syntax, which makes the code confusing, lengthy, complex and less readable. The simple solution to this issue is use of typedef. It is like an alias of struct.

### Code without typedef
```c
struct home_address {
  int local_street;
  char *town;
  char *my_city;
  char *my_country;
};
...
struct home_address var; 
var.town = "Agra";
```
Code using tyepdef
```c
typedef struct home_address{
  int local_street;
  char *town;
  char *my_city;
  char *my_country;
}addr;
..
..
addr var1;
var.town = "Agra";
```
Instead of using the struct home_address every time you need to declare struct variable, you can simply use addr, the typedef that we have defined.

## Example Program for c Typdef:
```c
// Structure using typedef:
 
#include <stdio.h>
#include <string.h>
 
typedef struct student 
{
  int id;
  char name[20];
  float percentage;
} status;
 
int main() 
{
  status record;
  record.id=1;
  strcpy(record.name, "Raju");
  record.percentage = 86.5;
  printf(" Id is: %d \n", record.id);
  printf(" Name is: %s \n", record.name);
  printf(" Percentage is: %f \n", record.percentage);
  return 0;
}
```
## Declaring an array of structure is same as declaring an array of fundamental types. Since an array is a collection of elements of the same type. In an array of structures, each element of an array is of the structure type.

Let’s take an example:
```c
struct car
{
    char make[20];
    char model[30]; 
    int year;
};
```
Here is how we can declare an array of structure car.

```c
struct car arr_car[10];
```
![image](https://user-images.githubusercontent.com/47218880/73758771-ae825200-4730-11ea-8fea-7255bcdb018f.png)

```c
#include<stdio.h>
#include<string.h>
#define MAX 2
 
struct student
{
    char name[20];
    int roll_no;
    float marks;
};
 
int main()
{
    struct student arr_student[MAX];
    int i;
 
    for(i = 0; i < MAX; i++ )
    {
        printf("\nEnter details of student %d\n\n", i+1);
 
        printf("Enter name: ");
        scanf("%s", arr_student[i].name);
 
        printf("Enter roll no: ");
        scanf("%d", &arr_student[i].roll_no);
 
        printf("Enter marks: ");
        scanf("%f", &arr_student[i].marks);
    }
 
    printf("\n");
 
    printf("Name\tRoll no\tMarks\n");
 
    for(i = 0; i < MAX; i++ )
    {
        printf("%s\t%d\t%.2f\n",
        arr_student[i].name, arr_student[i].roll_no, arr_student[i].marks);
    }
 
    // signal to operating system program ran fine
    return 0;
}
```
## Expected Output:
```
Enter details of student 1
 
Enter name: Jim
Enter roll no: 1
Enter marks: 44
 
Enter details of student 2
 
Enter name: Tim
Enter roll no: 2
Enter marks: 76
 
Name Roll no Marks
Jim 1 44.00
Tim 2 76.00
```

## Initializing Array of Structures
We can also initialize the array of structures using the same syntax as that for initializing arrays. Let’s take an example:
```c
struct car
{
    char make[20];
    char model[30]; 
    int year;
};
struct car arr_car[2] = {
                            {"Audi", "TT", 2016},
                            {"Bentley", "Azure", 2002}
                        };

```
## EXAMPLE PROGRAM FOR DECLARING MANY STRUCTURE VARIABLE IN C:
In this program, two structure variables “record1″ and “record2″ are declared for same structure and different values are assigned for both structure variables. Separate memory is allocated for both structure variables to store the data.
```c
#include <stdio.h>
#include <string.h>
 
struct student 
{
     int id;
     char name[30];
     float percentage;
};
 
int main() 
{
     int i;
     struct student record1 = {1, "John", 90.5};
     struct student record2 = {2, "Paul", 93.5};
 
     printf("Records of STUDENT1: \n");
     printf("  Id is: %d \n", record1.id);
     printf("  Name is: %s \n", record1.name);
     printf("  Percentage is: %f \n\n", record1.percentage);
 
     printf("Records of STUDENT2: \n");
     printf("  Id is: %d \n", record2.id);
     printf("  Name is: %s \n", record2.name);
     printf("  Percentage is: %f \n\n", record2.percentage);
 
     return 0;
}
```
## OUTPUT:
```
Records of STUDENT1:
Id is: 1
Name is: John
Percentage is: 90.500000
Records of STUDENT2:
Id is: 2
Name is: Paul
Percentage is: 93.500000

```

























