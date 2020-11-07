1 
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

![first frogram output](/OutputImages/1.png)

___

2
```c
	
