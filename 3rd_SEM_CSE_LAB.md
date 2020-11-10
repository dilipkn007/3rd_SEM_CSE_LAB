1. Design, Develop and Implement a menu driven Program in C for the following array operations.
	- Creating an array of N Integer Elements
	- Display of array Elements with Suitable Headings
	- Inserting an Element (ELEM) at a given valid Position (POS)
	- Deleting an Element at a given valid Position (POS)
	- Exit.

	Support the program with functions for each of the above operations.


```C
#include <stdio.h>
#include <stdlib.h>
int N, a[50], i, ELEM, POS;
void create()
{
	printf("Enter the size of the array(N) : ");
	scanf("%d", &N);
	printf("Enter %d array elements : ",N);
	for (i = 0; i < N; i++)
		scanf("%d", &a[i]);
}
void display()
{
	printf("The array elements are : ");
	for (i=0; i<N; i++)
		printf("%d\t", a[i]);
	printf("\n");
}
void insert()
{
	int i;
	printf("Enter the element(ELEM) to be inserted and its position(POS) respectively : "); 
	scanf("%d%d", &ELEM,&POS);
	for(i=N-1; i >= POS; i--)
		a[i+1]=a[i];
	a[POS]=ELEM;
	N++;
	printf("%d successfully inserted\n", ELEM);
}
void delete()
{
	printf("Enter the position(starting from 0) of element to be deleted : ");
	scanf("%d", &POS);
	for (i=POS; i<N; i++)
		a[i]=a[i+1];
	N--;	
	printf("The element at position %d successfully deleted\n", POS);
}
int main()
{
	int choice;
	printf("Enter \n\t1 to create an array\n\t2 to display the array\n\t3 to insert the element in the array\n\t4 to delete an element in an array\n\t0 to exit\n\n");
	while(1)
	{
		printf("\n\t\tEnter your choice --> ");
		scanf("%d", &choice);
		switch (choice)
		{
		case 1:
			create();
			break;
		case 2:
			display();
			break;
		case 3:
			insert();
			break;
		case 4:
			delete ();
			break;
		case 0:
			exit(0);
			break;
		default:
			printf("invalid choice\n");
		}
	}
	return 0;
}
```

### Output

![first frogram output](/OutputImages/1.png "1")

___

2. Design, Develop and Implement a Program in C for the following operations on Strings.
	- Read a main String (STR), a Pattern String (PAT) and a Replace String (REP)
	- Perform Pattern Matching Operation: Find and Replace all occurrences of PAT in STR with REP if PAT exists in STR. Report suitable messages in case PAT does not exist in STR

	Support the program with functions for each of the above operations. Don't use Built-in functions.

```c	
#include<stdio.h>
char STR[100],PAT[100],REP[100],ANS[100];
int i,j,c,m,k,flag=0;
void read()
{
	printf("\nEnter the MAIN string : ");
	gets(STR);
	printf("\nEnter the PATTERN string which has to be replaced : ");
	gets(PAT);
	printf("\nEnter the string to REPLACE : ");
	gets(REP);
}
void replaceSubstring()
{
	i=m=c=j=k=0;
	while( STR[c] != '\0')
	{
		 if ( STR[m] == PAT[i] )
		{
		 	m++; i++; 
		 	flag=1;
		 	if ( PAT[i] == '\0')
		 		{
		 		  for(k=0; REP[k] != '\0';k++,j++)
		 		  	ANS[j]=REP[k];
		 		  i=0;
		 		  c=m;
		 		}
		}
		else
		{
			ANS[j] = STR[c]; 
			j++; c++; m++;
			i=0;
		}
	}
	if(flag==0)
	{
		printf("\nPattern doesn't found!!!");
	}
	else
	{
		ANS[j] = '\0';
		printf("\nThe RESULTANT string is : %s\n" ,ANS);
	}
}
int main()
{
	read(); replaceSubstring();	
}
```

### Output

![first frogram output](/OutputImages/2.png "2")

___

3. Design, Develop and Implement a menu driven Program in C for the following operations on STACK of Integers (Array Implementation of Stack with maximum size MAX)
	- Push an Element on to Stack
	- Pop an Element from Stack
	- Demonstrate how Stack can be used to check Palindrome
	- Demonstrate Overflow and Underflow situations on Stack
	- Display the status of Stack
	- Exit
	
	Support the program with appropriate functions for each of the above operations.

```c

#include<stdio.h>
#include<stdlib.h>
#include<math.h>
#define max_size 5
int i,n,keep,rem,num[max_size],stack[max_size],tos=-1;
void push(int n)
{
	stack[++tos]=n;
}
int pop()
{
	return stack[tos--];
}
void palindrome()
{
	tos=-1;
	printf("\nEnter the number to be checked : ");
	scanf("%d",&keep);
	n=keep;
	while(n!=0)
	{
		rem=n%10;
		push(rem);
		n=n/10;
	}
	for(i=0;tos!=-1;i++)
		n=n+pop()*pow(10,i);
	if(keep==n)
		printf("Palindrome\n");
	else	  
		printf("Not Palindrome\n");
}
void display()
{
	for(i=tos;i>=0;i--)
		printf("\t\t\t\t|%d|\n",stack[i]);
} 
int main()
{
	int choice;
	printf("\nEnter\n\t\t1 to Push the element to the stack\n\t\t2 to Pop the stack element\n\t\t3 to check for Palindrome\n\t\t4 to Display the stack element\n\t\t5 to Exit\n");
    while(1)
    {
    	printf("\n\nEnter your choice ---> ");
    	scanf("%d",&choice);
        switch(choice)
        {
        	case 1: if(max_size-1==tos)
							printf("\nStack overflow");
						else
							{
								printf("\nEnter the element to be pushed : ");
								scanf("%d",&n);
								push(n);
							}
        	break;
        	case 2: if(tos==-1)
							printf("\nStack Underflow");
						else
							printf("\nPopped element is %d",pop());
        	break;
        	case 3: palindrome();
        	break;
        	case 4: if(tos==-1)
							printf("\nThe stack is empty");
						else
							display();
        	break;
        	case 5: exit(0);
        	break;
        	default: printf("\nInvalid choice:\n");
        }
    }
return 0;
}
```

### Output

![Third program output](/OutputImages/3.png "3")

___

4. Design, Develop and Implement a Program in C for converting an Infix Expression to Postfix Expression. Program should support for both parenthesized and free parenthesized expressions with the operators: +, -, *, /, % (Remainder), ^ (Power) and alphanumeric operands.

```c

```

### Output

![Third program output]()

___

5. Design, Develop and Implement a Program in C for the following Stack Applications.
	- Evaluation of Suffix expression with single digit operands and operators: +, -, *, /, %,^.
	- Solving Tower of Hanoi problem with n disks.

```c

```

### Output

![Third program output]()

___	

6. Design, Develop and Implement a menu driven Program in C for the following operations on Circular QUEUE of Characters (Array Implementation of Queue with maximum size MAX).
	- Insert an Element on to Circular QUEUE
	- Delete an Element from Circular QUEUE
	- Demonstrate Overflow and Underflow situations on Circular QUEUE
	- Display the status of Circular QUEUE
	- Exit

	Support the program with appropriate functions for each of the above operations

```c

```

### Output

![Third program output]()

___	

7. Design, Develop and Implement a menu driven Program in C for the following operations on Singly Linked List (SLL) of Student Data with the fields: USN, Name, Programme, Sem,PhNo.
	- Create a SLL of N Students Data by using front insertion.
	- Display the status of SLL and count the number of nodes in it
	- Perform Insertion / Deletion at End of SLL
	- Perform Insertion / Deletion at Front of SLL(Demonstration of stack)
	- Exit

```c

```

### Output

![Third program output]()

___	

8. Design, Develop and Implement a menu driven Program in C for the following operations on Doubly Linked List (DLL) of Employee Data with the fields: SSN, Name, Dept, Designation,Sal, PhNo
	- Create a DLL of N Employees Data by using end insertion.
	- Display the status of DLL and count the number of nodes in it
	- Perform Insertion and Deletion at End of DLL
	- Perform Insertion and Deletion at Front of DLL
	- Demonstrate how this DLL can be used as Double Ended Queue.
	- Exit

```c

```

### Output

![Third program output]()

___	

9. Design, Develop and Implement a Program in C for the following operationson Singly Circular Linked List (SCLL) with header nodes
	- Represent and Evaluate a Polynomial P(x,y,z) = 6x<sup>2</sup>y<sup>2</sup>z-4yz<sup>5</sup>+3x<sup>3</sup>yz+2xy<sup>5</sup>z-2xyz<sup>3</sup>
	- Find the sum of two polynomials POLY1(x,y,z) and POLY2(x,y,z) and store the
result in POLYSUM(x,y,z)

	Support the program with appropriate functions for each of the above operations.

```c

```

### Output

![Third program output]()

___

10. Design, Develop and Implement a menu driven Program in C for the following operations on Binary Search Tree (BST) of Integers.
	- Create a BST of N Integers: 6, 9, 5, 2, 8, 15, 24, 14, 7, 8, 5, 2
	- Traverse the BST in Inorder, Preorder and Post Order
	- Search the BST for a given element (KEY) and report the appropriate message
	- Exit

```c

```

### Output

![Third program output]()

___

11. Design, Develop and Implement a Program in C for the following operations on Graph(G) of Cities.
	- Create a Graph of N cities using Adjacency Matrix.
	- Print all the nodes reachable from a given starting node in a digraph using DFS/BFS method.

```c

```

### Output

![Third program output]()

___

12. Given a File of N employee records with a set K of Keys (4-digit) which uniquely determine the records in file F. Assume that file F is maintained in memory by a Hash Table (HT) of m memory locations with L as the set of memory addresses (2-digit) of locations in HT. Let the keys in K and addresses in L are Integers. Design and develop a Program in C that uses Hash function H: K ®L as H(K)=K mod m (remainder method), and implement hashing technique to map a given key K to the address space L. Resolve the collision (if any) using linear probing.

```c

```

### Output

![Third program output]()

___
