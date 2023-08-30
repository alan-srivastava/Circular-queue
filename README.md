//# Circular-queue
//Code in c to design a circular queue. 
#include<stdio.h>
#define MAX 5
int in(int [],int ,int );
int de(int [],int ,int );
void dis(int [],int ,int );
void peek(int [],int ,int );
int main(){
	int cq[MAX],front=-1,rear=-1,n;
	do{
		printf("\n-------------------------------------------QUEUE------------------------------------------------------\n");
		printf("\n1.INQUE\n2.DEQUE\n3.DISPLAY\n4.PEEK VALUE\n5.EXIT\n");
		printf("Select the Option you want to Perform:-");
		scanf("%d",&n);
		printf("--------------------------------------------------------------------------------------------------------\n");
		switch(n)
		{
			case 1:
				rear=in(cq,front,rear);
				if(front==-1)
				{
					front=0;
				}
				break;
			case 2:
				front=de(cq,front,rear);
				break;
			case 3:
				dis(cq,front,rear);
				break;
			case 4:
				peek(cq,front,rear);
				break;
		}
	}while(n!=5);
	return 0;
}
int in(int cq[],int front,int rear)
{
	if((rear+1)%MAX==front)
	{
		printf("Queue Overflow.\n");
	}
	else
	{
		int n;
		rear=(rear+1)%MAX;
		printf("Enter the Value:-");
		scanf("%d",&n);
		cq[rear]=n;
	}
return rear;
}
int de(int cq[],int front,int rear)
{
	int n;
	if((rear==-1)&&(front==-1))
	
		printf("Queue is Empty.\n");
	
	else
	{
	    n=cq[front];
	    printf("dequed element is %d",n);
		if(front==rear)
		{
			rear=-1;
			front=-1;
		}
			front=(front+1)%MAX;
		}
		return front;
	}


void dis(int cq[],int front,int rear)
{
	if((front==-1)&&(rear==-1))
	{
		printf("Queue is Empty.\n");
	}
	else
	{
		int i;
		printf("Elements in the Queue are:-");
		for(i=front;i!=rear;i=((i+1)%MAX))
		{
			printf("%5d",cq[i]);
		}
		printf("%5d",cq[i]);
	}
}
void peek(int cq[],int front,int rear)
{
	if((front==-1)&&(rear==-1))
	{
		printf("Queue is Empty.\n");
	}
	else
	{
		printf("%d\n",cq[front]);
	}
}
