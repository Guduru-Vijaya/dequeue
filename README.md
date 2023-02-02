#include <stdio.h>
#include <stdlib.h>
struct queue
{
	int data;
	struct queue * next;
};
void ins_beg(struct queue **,struct queue **);
void ins_end(struct queue **,struct queue **);
void rem_beg(struct queue **,struct queue **);
void rem_end(struct queue **,struct queue **);
void display(struct queue **,struct queue **);
int main()
{
	struct queue *f = NULL;
	struct queue *r = NULL;
	int o,o1;
	do
	{
		printf("\n--OPTIONS--\n1)Ins at beg\n2ins at end\n3)Del at beg\n4)del at end\n5)Display.\nEnter an Option\t: ");
		scanf("%d",&o);
		switch(o)
		{
		
			case 1:
				ins_beg(&f,&r);
				break;
				
			case 2:
				ins_end(&f,&r);
				break;
	
	        
	        case 3:if(f!=NULL)
			{
				    rem_beg(&f,&r);
				    break;
			}
			else
	        {
	        	printf("\nQueue is Empty!!\n");
	        }
			case 4:if(f!=NULL)
			{
				    rem_end(&f,&r);
				    break;
			}
			else
	        {
	        	printf("\nQueue is Empty!!\n");
	        }
	        case 5:
	        if(f!=NULL)
	        {
	        	display(&f,&r);
	        }
	        else
	        {
	        	printf("\nQueue is Empty!!\n");
	        }
	        break;
		}
	}while((o<=5)&(o!=0));
}
void ins_beg(struct queue **f,struct queue **r)
{
	int ele;
	struct queue *p;
	p = (struct queue *)malloc(sizeof(struct queue));
	printf("\nEnter an element : ");
	scanf("%d",&ele);
	p->data = ele;
	p->next = NULL;
	if((*f)==NULL)
	{
		(*f) = p;
		(*r) = (*f);
	}
	else
	{
		p->next = (*f);
		(*f) = p;
	}
}
void ins_end(struct queue **f,struct queue **r)
{
	int ele;
	struct queue *p;
	p = (struct queue *)malloc(sizeof(struct queue));
	printf("\nEnter an element : ");
	scanf("%d",&ele);
	p->data = ele;
	p->next = NULL;
	if((*f)==NULL)
	{
		(*f) = p;
		(*r) = (*f);
	}
	else
	{
		(*r)->next = p;
		(*r) = p;
	}
}
void rem_beg(struct queue **f,struct queue **r)
{
	struct queue * p;
	p = (*f);
	printf("\nRenoved - %d\n",p->data);
	(*f) = (*f)->next;
	free(p);
}
void rem_end(struct queue **f,struct queue **r)
{
	struct queue * p;
	if((*f)->next==NULL)
	{
		p = (*f);
		printf("\nRemoved - %d\n",p->data);
		(*f) = NULL;
	}
	else
	{
	    p = (*f);
	    while(p->next->next!=NULL)
	    {
	    	p = p->next;
	    }
	    printf("\nRemoved - %d\n",(*r)->data);
	    (*r) = p;
		(*r)->next = NULL;
	}
	free(p);
}
void display(struct queue **f,struct queue **r)
{
	struct queue * q;
	q = (*f);
	printf("\n");
	while(q!=NULL)
	{
		printf("%d ",q->data);
		q = q->next;
	}
	printf("\n");
}
