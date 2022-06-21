# Queue
* array
```
#include<stdio.h>
#include<stdlib.h>

int n=2,rear=-1,front=-1;
int queue[100];

//to check if queue is full
int isfull()
{
	if(rear==n-1)
		return 1;
	else
		return 0;
}

//to check if queue is empty
int isempty()
{
	if(rear==front)
		return 1;
	else
		return 0;
}

//to insert element into queue
void enqueue(int val)
{
	if(isfull())
		printf("\nOverflow");
	else
	{
		rear++;
		queue[rear]=val;
		printf("\n%d enqueued",queue[rear]);
	}
}

//to delete element from queue
void dequeue()
{
	if(isempty())
		printf("\nUnderflow");
	else
	{
		printf("\n%d dequeued",queue[front+1]);
		queue[front]=-1;
		front++;
	}
}

//to display elements
void display()
{
	if(isempty())
		printf("\nEmpty queue");
	else
	{	
		printf("\nElements are: ");
		for(int i=front+1;i<=rear;i++)
			printf("%d ",queue[i]);
	}
}

//to find the rear of queue
void findrear()
{
	printf("\nrear position=%d\nrear value=%d",rear,queue[rear]);
}

//to reset queue pointers
void queuereset()
{
	if(isempty() && isfull())
	{
		front=-1;
		rear=-1;
	}
}

void main()
{
	int ch,entry;
	int extern n;
	printf("Enter queue size");
	scanf("%d",&n);
	while(1)
	{
		//      MENU
		printf("\n\n1:enqueue\n2:dequeue\n3:DISPLAY\n4:Is queue Empty\n5:Is queue Full\n6:Find rear\n7:Exit\nEnter your choice: ");
		scanf("%d",&ch);
		queuereset();
		switch(ch)
		{
			case 1:
			{
				printf("Enter data");
				scanf("%d",&entry);
				enqueue(entry);
				break;
			}
			
			case 2:
			{
				dequeue();
				break;
			}
			
			case 3:
			{
				display();
				break;
			}
			
			case 4:
			{
				if(isempty())
					printf("\nqueue is Empty");
				else
					printf("\nqueue is not Empty ");
				break;
			}
			
			case 5:
			{
				if(isfull())
					printf("\nqueue is Full");
				else
					printf("\nqueue is not Full ");
				break;
			}
			
			case 6:
			{
				findrear();
				break;
			}
			
			case 7:
			{
				printf("Exiting...");
				exit(0);
			}
			
			default:
			{
				printf("Invalid choice");
			}
		}
	}
}
```
* linklist
```
#include<stdio.h>
#include<stdlib.h>
int size=4,r=-1;


struct node
{
	int data;
	struct node *next;
};


struct node *front=NULL,*pos=NULL,*rear=NULL,*temp;

int isfull()
{
	if(r==size-1)
		return 1;
	else
		return 0;
}

int isempty()
{
	if(front==NULL)
		return 1;
	else
		return 0;
}


void enqueue(int val)
{
	if(isfull())
	{
		printf("\nOverflow");
	}
	else if(isempty())
	{
		front=(struct node*)malloc(sizeof(struct node));
		front->data=val;
		rear=front;
		printf("\n%d enqueued",front->data);
		r++;
		
	}
	else
	{	
		temp=(struct node*)malloc(sizeof(struct node));
		temp->data=val;
		rear->next=temp;
		rear=temp;
		printf("\n%d enqueued",rear->data);
		r++;
	}
	
	
}

void dequeue()
{
	if(isempty())
	{
		printf("Underflow");
	}
	else
	{
		temp=front;
		front=front->next;
		temp->next=NULL;
		printf(" %d dequeued",temp->data);
		free(temp);
		r--;		
	}
}

void display()
{	
	int j,i;
	
	if(isempty())
	{
		printf("Empty Queue");
	}
	else
	{
		
		pos=front;
		while(pos!=NULL)
		{
			printf("%d ",pos->data);
			pos=pos->next;
		}
		
	}
}

void findrear()
{
	printf("\nrear position=%d\n",r);
	if(front==NULL)
		printf("rear value=NULL");
	else
		printf("rear value=%d",rear->data);
}

void main()
{
	int ch,entry;
	
	printf("Enter queue Size :");
	scanf("%d",&size);
	
	while(1)
	{
		printf("\n\n1:ENQUEUE\n2:DEQUEUE\n3:DISPLAY\n4:Is queue Empty\n5:Is queue Full\n6:Find REAR\n7:Exit\nEnter your choice: ");
		scanf("%d",&ch);
		switch(ch)
		{
			case 1:
			{
				printf("Enter data :");
				scanf("%d",&entry);
				enqueue(entry);
				break;
			}
			
			case 2:
			{
				dequeue();
				break;
			}
			
			case 3:
			{
				display();
				break;
			}
			
			case 4:
			{
				if(isempty())
					printf("\nqueue is Empty");
				else
					printf("\nqueue is not Empty ");
				break;
			}
			
			case 5:
			{
				if(isfull())
					printf("\nqueue is Full");
				else
					printf("\nqueue is not Full ");
				break;
			}
			
			case 6:
			{
				findrear();
				break;
			}
			
			case 7:
			{
				printf("Exiting...");
				exit(0);
			}
			
			default:
			{
				printf("Invalid choice");
			}
		}
	}
}
```
