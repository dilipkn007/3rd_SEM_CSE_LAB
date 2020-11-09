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

```

### Output

![Third program output]()

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