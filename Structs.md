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


































