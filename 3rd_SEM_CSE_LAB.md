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
			j++; c++; m=c;
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
						printf("\nEnter theelement to be pushed :");
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
#include<stdio.h>
#include<string.h>
char stack[50],sym;
int tos=-1;
void push(char a)
{
    stack[++tos]=a;
}
char pop()
{
    return stack[tos--];
}
int precidence(char sym)
{
  switch (sym)
  {
  case '#': case '(' : case ')':       return 1;
  case '+':case '-':        return 2;
  case '*': case '/':case '%':        return 3;
  case '^':        return 4;          
  }
}
void convert(char infix[50],char postfix[50])
{
    int i,j=0;
    push('#');
    for(i=0;i<strlen(infix);i++)
    {
        sym=infix[i];
        switch (sym)
        {
        case '(':push(sym);
            break;
        case ')':while (stack[tos]!='(')
                    postfix[j++]=pop();
                    pop();  
                    break;
        case '*':case '/':case '%':case '+':case '-':case '^':while (precidence(sym)<=precidence(stack[tos]))
                                                                                    postfix[j++]=pop();
                                                              push(sym);
                                                              break;
        default:postfix[j++]=sym;
            break;
        }
    }           
    while (stack[tos]!='#')
            postfix[j++]=pop(); 
            postfix[j]='\0';
}
int main()
{   
    char infix[50],postfix[50];
    printf("Enter the expression : \n");
    scanf("%s",infix);
    convert(infix,postfix);
    printf("The post fix of the given expression is %s",postfix);
    return 0;
}
```

### Output

![Third program output](/OutputImages/4.png "4")

___

5. Design, Develop and Implement a Program in C for the following Stack Applications.
	- Evaluation of Suffix expression with single digit operands and operators: +, -, *, /, %,^.
	- Solving Tower of Hanoi problem with n disks.

```c
#include<stdio.h>
#include<stdlib.h>
#include<string.h>
#include<math.h>
#include<ctype.h>
float stack[20];
int tos=-1;
void push(char c)
{
    stack[++tos]=c;
}
float pop()
{
    return stack[tos--];
}
float evaluatePostfix(char postfix[])
{
    char symb;
    float op1,op2,num;
    for (int i = 0; i < strlen(postfix); i++)
    {
        symb=postfix[i];
        if(isdigit(symb))
            push(symb-'0');
        else if(isalpha(symb))
        {
            printf("\nEnter the value of %c : ",symb);
            scanf("%f",&num);
            push(num);
        }
        else
        {
            op2=pop(); op1=pop();
            switch (symb)
            {
            case '+':push(op1+op2); break;
            case '-':push(op1-op2); break;
            case '*':push(op1*op2); break;
            case '/':push(op1/op2); break;
            case '%':push(remainder(op1,op2)); break;
            case '^':push(pow(op1,op2)); break;
            default:
                printf("\nInvalid Expression");
                exit(0);
                break;
            }
        }
    }
    return pop();
}
int main()
{
    char postfix[20];
    printf("\nEnter the Suffix expression(single digit operands) :");
    scanf("%s",postfix);
    printf("\nThe result of the expression is %f",evaluatePostfix(postfix));
    return 0;
}
```

### Output

![Third program output](/OutputImages/5a1.png "5a1")
![Third program output](/OutputImages/5a2.png "5a2")

```c
#include<stdio.h>
void tower(int n,char from,char to,char aux)
{
    if(n==1)
    {
        printf("\nMove disk 1 from %c to %c",from,to);
        return;
    }
    tower(n-1,from,aux,to);
    printf("\nMove disk 1 from %c to %c",from,to);
    tower(n-1,aux,to,from);
}
int main()
{
    int n;
    printf("\nEnter number of disks : ");
    scanf("%d",&n);
    printf("\nFollow this sequence to move from peg A to peg B :- \n");
    tower(n,'A','B','C');
    return 0;
}
```

### Output

![Third program output](/OutputImages/5b.png "5a1")

___	

6. Design, Develop and Implement a menu driven Program in C for the following operations on Circular QUEUE of Characters (Array Implementation of Queue with maximum size MAX).
	- Insert an Element on to Circular QUEUE
	- Delete an Element from Circular QUEUE
	- Demonstrate Overflow and Underflow situations on Circular QUEUE
	- Display the status of Circular QUEUE
	- Exit

	Support the program with appropriate functions for each of the above operations

```c
#include<stdio.h>
#include<stdlib.h>
#define size 5
int q[size],f=-1,r=-1;
void enqueue(int e)
{
	r=(r+1)%size;
	q[r]=e;	
}
int dequeue()
{
	f=(f+1)%size;
	return q[f];
}
void display()
{
	if(f==r)
		printf("\nQueue is empty");
	else
	{
		int i=f+1;
		do
		{
			printf("%d\t",q[i]);
			i=(i+1)%size;
		} while (i!=(r+1)%size);
	}
}
int main()
{
	int ch,e;
	printf("\nEnter\n\t\t1 to add an element in the Queue\n\t\t2 to delete an element in the Queue\n\t\t3 to display the queue\n\t\t4 to exit");
	while(1)
	{
		printf("\nEnter your choice----->");
		scanf("%d",&ch);
		switch(ch)
		{
			case 1: 
				if((r+1)%size==f || (r==size-1 && f==-1))
					printf("\nQueue is full");
				else
				{
					printf("\nEnter the element : ");
					scanf("%d",&e);
					enqueue(e);
				}
				break;
			case 2:
	 			if(f==r)
	 				printf("\nQueue is empty");
	 			else
					printf("\nDeleted element is %d",dequeue());
				break;
			case 3:
				display();
				break;
			case 4:
				exit(0)	;
			default:
				printf("\nInvalid Choice");
				break;
		}
	}
	return 0;
}
```

### Output

![Third program output](/OutputImages/6.png)

___	

7. Design, Develop and Implement a menu driven Program in C for the following operations on Singly Linked List (SLL) of Student Data with the fields: USN, Name, Programme, Sem,PhNo.
	- Create a SLL of N Students Data by using front insertion.
	- Display the status of SLL and count the number of nodes in it
	- Perform Insertion / Deletion at End of SLL
	- Perform Insertion / Deletion at Front of SLL(Demonstration of stack)
	- Exit

```c
#include<stdio.h>
#include<stdlib.h>
typedef struct SLL
{
    long long int PhNo;
    char SEM[5],name[50],USN[10],Program[10];
    struct SLL *next;
}node;
node *start=NULL;
node* getnode()
{
    char u[10];
    node *p;
    p=(node *)malloc(sizeof(node));
    printf("Enter Name, USN, SEM, program and phone number of the student respectively : ");
    scanf("%s%s%s%s%lld",p->name,p->USN,p->SEM,p->Program,&(p->PhNo));
    p->next=NULL;
    return p; 
}
void Ins_front()
{
    node *p;
    p=getnode();
    p->next=start;
    start=p;
}
void  Del_front()
{
   node *temp=start;
   if(start==NULL)
   {
     printf("List is empty ");
     return;
   }
   start=start->next;
   printf("The %s student's data is deleted\n",temp->USN);
   free(temp);
}
void display()
{
    int count=0;
    node *temp=start;
    if(temp==NULL)
    {
      printf("List is empty\n");
      return;
    }
    printf("\n\t\tName\t\tUSN\t\tSEM\t\tProgram\t\tPhone number");  
    while(temp!=NULL)
    {
        printf("\n\t\t%s\t\t%s\t\t%s\t\t%s\t\t%lld",temp->name,temp->USN,temp->SEM,temp->Program,temp->PhNo);
        temp=temp->next;
        count++;
    }
    printf("\n\t\tThere are %d nodes \n",count);
}
void Ins_end()
{
  node *p,*temp=start;
  p=getnode();
  if(start==NULL)
  {
    start=p;
    return;
  }
  while (temp->next!=NULL)
    temp=temp->next;
  temp->next=p;  
}
void Del_end()
{
   node *temp=start,*prev;
   if(start==NULL)
   {
     printf("List is empty ");
     return;
   }
   while (temp->next!=NULL)   
   {
     prev=temp;
     temp=temp->next;
   }
   prev->next=NULL;
   printf("The %s student's data is deleted\n",temp->USN);
   free(temp);
}
int main()
{
    int n,i,op;
    printf("Enter\n\t\t1 to Create a SLL of N Students Data by using front insertion.\n\t\t2 to Display the status of SLL and count the number of nodes in it.\n\t\t3 to Insert the node at front of SLL\n\t\t4 to Delete the node at front of SLL\n\t\t5 to Insert the node at end of SLL\n\t\t6 to Delete the node at end of SLL\n\t\t7 to exit");
    while(1)
    {
         printf("\n\t\tEnter your choice -->");
            scanf("%d",&op);
        switch(op)
        {
        case 1:
            printf("Enter the number of students : ");
            scanf("%d",&n);
            for(i=0;i<n;i++)
                Ins_front();
            break;
        
        case 2:
            display();
            break;

        case 3:
            Ins_front();
            break;

        case 4:
            Del_front();
            break;

        case 5:
            Ins_end();
            break;

        case 6:
            Del_end();
            break;

        case 7:
            exit(0);

        default:
            break;
        }
    }
    return 0;
}
```

### Output

![Third program output](/OutputImages/7.png)

___	

8. Design, Develop and Implement a menu driven Program in C for the following operations on Doubly Linked List (DLL) of Employee Data with the fields: SSN, Name, Dept, Designation,Sal, PhNo
	- Create a DLL of N Employees Data by using end insertion.
	- Display the status of DLL and count the number of nodes in it
	- Perform Insertion and Deletion at End of DLL
	- Perform Insertion and Deletion at Front of DLL
	- Demonstrate how this DLL can be used as Double Ended Queue.
	- Exit

```c
#include<stdio.h>
#include<stdlib.h>
typedef struct DLL
{
    struct DLL *prev;
    long long int PhNo;
    int sal;
    char name[50],SSN[10],Dept[10], designation[20];
    struct DLL *next;
}node;
node *start=NULL;
node* getnode()
{
    node *p;
    p=(node *)malloc(sizeof(node));
    printf("Enter Name, Employee No, Department, salary, phone number and designation of the employee respectively : ");
    scanf("%s%s%s%d%lld%s",p->name,p->SSN,p->Dept,&(p->sal),&(p->PhNo),p->designation);
    p->prev=p->next=NULL;
    return p; 
}
void Ins_front()
{
    node *p;
    p=getnode();
    if (start==NULL)
    {
      start=p;
      return;
    }
    p->next=start;
    start->prev=p;
    start=p;
}
void  Del_front()
{
   node *temp=start;
   if(start==NULL)
   {
     printf("List is empty ");
     return;
   }
   start=start->next;
   printf("The %s employee's data is deleted\n",temp->SSN);
   free(temp);
   start->prev=NULL;
}
void display()
{
    int count=0;
    node *temp=start;
    if(temp==NULL)
    {
      printf("List is empty\n");
      return;
    }
    printf("\n\tName\tEmployee No\tDepartment\tsalary\t\tphone number\tdesignation");  
    while(temp!=NULL)
    {
        printf("\n\t%s\t%s\t\t%s\t\t%d\t\t%lld\t%s",temp->name,temp->SSN,temp->Dept,temp->sal,temp->PhNo,temp->designation);
        temp=temp->next;
        count++;
    }
    printf("\n\t\tThere are %d nodes \n",count);
}
void Ins_end()
{
  node *p,*temp=start;
  p=getnode();
  if(start==NULL)
  {
    start=p;
    return;
  }
  while (temp->next!=NULL)
    temp=temp->next;
  temp->next=p;  
  p->prev=temp;
}
void Del_end()
{
   node *temp=start,*prev;
   if(start==NULL)
   {
     printf("List is empty ");
     return;
   }
   while (temp->next!=NULL)   
     temp=temp->next;
   (temp->prev)->next=NULL;
   printf("The %s Employees's data is deleted\n",temp->SSN);
   free(temp);
}
int main()
{
    int n,i,op;
    printf("Enter\n\t\t1 to Create a DLL of N Employees Data by using end insertion.\n\t\t2 to Display the status of DLL and count the number of nodes in it.\n\t\t3 to Insert the node at front of DLL\n\t\t4 to Delete the node at front of DLL\n\t\t5 to Insert the node at end of DLL\n\t\t6 to Delete the node at end of DLL\n\t\t7 to exit");
    while(1)
    {
         printf("\n\t\tEnter your choice -->");
            scanf("%d",&op);
        switch(op)
        {
        case 1:
            printf("Enter the number of Employees : ");
            scanf("%d",&n);
            for(i=0;i<n;i++)
                Ins_end();
            break;
        
        case 2:
            display();
            break;

        case 3:
            Ins_front();
            break;

        case 4:
            Del_front();
            break;

        case 5:
            Ins_end();
            break;

        case 6:
            Del_end();
            break;

        case 7:
            exit(0);

        default:
            printf("\nInvalid Choice");
            break;
        }
    }
    return 0;
}
```

### Output

![Third program output](/OutputImages/8.png)

___	

9. Design, Develop and Implement a Program in C for the following operationson Singly Circular Linked List (SCLL) with header nodes
	- Represent and Evaluate a Polynomial P(x,y,z) = 6x<sup>2</sup>y<sup>2</sup>z-4yz<sup>5</sup>+3x<sup>3</sup>yz+2xy<sup>5</sup>z-2xyz<sup>3</sup>
	- Find the sum of two polynomials POLY1(x,y,z) and POLY2(x,y,z) and store the
result in POLYSUM(x,y,z)

	Support the program with appropriate functions for each of the above operations.

```c
#include <stdio.h>
#include <malloc.h>
#include <math.h>
#include <conio.h>
typedef struct poly
{
  int c, e1, e2, e3, flag;
  struct poly *next;
} node;
void insEnd(node *h, int c, int e1, int e2, int e3);
void readPoly(node *h);
void addPoly(node *h1, node *h2, node *h3);
void display(node * h);
void evaluate(node * h3);
int main()
{
  node *h1, *h2, *h3;
  h1 = (node *)malloc(sizeof(node));
  h1->next = h1;
  h2 = (node *)malloc(sizeof(node));
  h2->next = h2;
  h3 = (node *)malloc(sizeof(node));
  h3->next = h3;
  printf("\nFirst polynomial :  ");
  readPoly(h1);
  printf("\nSecond polynomial :  ");
  readPoly(h2);
  addPoly(h1,h2,h3);
  printf("\n1st poly:\t");
  display(h1);
  printf("\n2nd poly:\t");
  display(h2);
  printf("\n\t\t----------");
  printf("\nSum:\t\t");
  display(h3);
  evaluate(h3);
  return 0;
}
void insEnd(node *h, int c, int e1, int e2, int e3)
{
  node *temp = h->next, *n = (node *)malloc(sizeof(node));
  n->next=n;
  n->c = c;
  n->e1 = e1;
  n->e2 = e2;
  n->e3 = e3;
  n->next = h;
  n->flag = 0;
  while (temp->next != h)
    temp = temp->next;
  n->next = temp->next;
  temp->next = n;
}
void readPoly(node *h)
{
  int c, e1, e2, e3;
  char ch;
  do
  {
    printf("\nEnter coefficients, exponent 1, exponent 2 and exponent 3: ");
    scanf("%d%d%d%d",&c, &e1, &e2, &e3);
    insEnd(h, c, e1, e2, e3);
    printf("\nDo you want to add another term Y/N:  ");
    ch=getche();
  } while (ch == 'y' || ch == 'Y');
}
void addPoly(node *h1, node *h2, node *h3)
{
  node *p1 = h1->next, *p2;
  int x;
  while (p1 != h1)
  {
    p2 = h2->next;
    while (p2!=h2)
    {
      if (p1->e1 == p2->e1 && p1->e2 == p2->e2 && p1->e3 == p2->e3 )
      {
        x = p1->c + p2->c;
        insEnd(h3, x, p1->e1, p1->e2, p1->e3);
        p1->flag = 1;
        p2->flag = 1;
      }
      p2 = p2->next;
    }
    p1 = p1->next;
  }
  p1 = p1->next;
  p2 = p2->next;
  while (p1 != h1)
  {
    if (p1->flag == 0)
      insEnd(h3, p1->c, p1->e1, p1->e2, p1->e3);
    p1 = p1->next;
  }
  while (p2 != h2)
  {
    if (p2->flag == 0)
      insEnd(h3, p2->c, p2->e1, p2->e2, p2->e3);
    p2 = p2->next;
  }
}
void display(node * h)
{
  node *p = h->next;
  if(p==h)
  {
    printf("\nList is empty");
    return;
  }
  while (p != h)
  {
    printf(" %+dx^%dy^%dz^%d ", p->c, p->e1, p->e2, p->e3);
    p = p->next;
  }
}
void evaluate(node * h3)
{
  node *p3 = h3->next;
  int x, y, z, sum = 0;
  printf("\nEnter the value of x, y and z : ");
  scanf("%d%d%d", &x, &y, &z);
  while (p3 != h3)
  {
    sum += p3->c * pow(x, p3->e1) * pow(y, p3->e2) * pow(z, p3->e3);
    p3 = p3->next;
  }
  printf("\nSolution = %d", sum);
}
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

![Third program output](/OutputImages/9.png)

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
