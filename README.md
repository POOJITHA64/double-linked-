# double-linked-
#include<stdio.h>
#include<stdlib.h>
struct node
{
    struct node *prev;
    int data;
    struct node *next;
}*newnode,*temp,*temp1;
struct node *head=NULL;
struct node *tail=NULL;
//Creation of Double linked list.
void create()
{
    int value,choice;
    do{
        newnode=(struct node*)malloc(sizeof(struct node));
        printf("Enter the value:\n");
        scanf("%d",&value);
        newnode->data=value;
        newnode->prev=NULL;
        newnode->next=NULL;
        if(head==NULL)
        {
            head=newnode;
            tail=newnode;
        }
        else
        {
            tail->next=newnode;
            newnode->prev=tail;
            tail=newnode;
        }
        printf("Press 1 to enter and others to exit()\n");
        fflush(stdin);
        scanf("%d",&choice);
    }
    while(choice==1);
}
//Display the double linked list.
void display()
{
    temp=head;
    while(temp!=NULL)
    {
        printf("# %d #",temp->data);
        temp=temp->next;
    }
   
}
//Insertion at beginning.
void insert_at_beg()
{
    int value;
    newnode=(struct node*)malloc(sizeof(struct node));
    printf("Enter the value to be inserted at beginning:\n");
    scanf("%d",&value);
    newnode->data=value;
    newnode->next=head;
    newnode->prev=NULL;
    head->prev=newnode;
    head=newnode;
}
//Insertion at ending.
void insert_at_end()
{
    int value;
    newnode=(struct node*)malloc(sizeof(struct node));
    printf("Enter the value to be inserted at ending:\n");
    scanf("%d",&value);
    newnode->data=value;
    tail->next=newnode;
    newnode->prev=tail;
    newnode->next=NULL;
    tail=newnode;
}
//Insertion at specified position.
void insert_at_pos()
{
    int value,position;
    newnode=(struct node*)malloc(sizeof(struct node));
    printf("Enter the value to be inserted at specified position:\n");
    scanf("%d",&value);
    printf("Enter the position to insert an element:\n");
    scanf("%d",&position);
    temp=head;
    for(int i=0;i<position-1;i++)
    {
        temp=temp->next;
    }
    newnode->data=value;
    newnode->next=temp->next;
    temp->next->prev=newnode;
    temp->next=newnode;
    newnode->prev=temp;
}
//Deletion at beginning.
void delete_at_beg()
{
    temp=head;
    head=head->next;
    temp->next=NULL;
    head->prev=NULL;
}
//Deletion at ending.
void delete_at_end()
{
    temp=tail;
    tail=temp->prev;
    temp->prev=NULL;
    tail->next=NULL;
}
//Deletion at specified position.
void delete_at_pos()
{
    int position,i;
    printf("Enter the position where the element is deleted:\n");
    scanf("%d",&position);
    temp=head;
    for(i=0;i<position-1;i++)
    {
        temp=temp->next;
    }
    temp1=temp->next;
    temp->next=temp1->next;
    temp->next->prev=temp;
    temp1->prev=NULL;
    temp1->next=NULL;
}
//To count the number of elements DLL.
void count()
{
    int count=0;
    temp=head;
    while(temp!=NULL)
    {
        printf("# %d #",temp->data);
        count+=1;
        temp=temp->next;
    }
    printf("\nThe number of elements present in DLL are:%d",count);
}
//Reversin of DLL.
void reverse()
{
    temp=tail;
    while(temp->prev!=NULL)
    {
        printf("# %d #",temp->data);
        temp=temp->prev;
    }
    printf("# %d #",temp->data);
}
//Main function.
void main()
{
    int choice=0;
    while(choice<11)
    {
        printf("\nOperations on double linked list.\n");
        printf("1.Creation of double linked list.\n");
        printf("2.Display of elements in double linked list.\n");
        printf("3.To insert an element at beginning.\n");
        printf("4.To insert an element at ending.\n");
        printf("5.To insert an element at specified position.\n");
        printf("6.To delete an element from the beginning.\n");
        printf("7.To delete an element from the ending.\n");
        printf("8.To delete an element from specified position.\n");
        printf("9.To count the number of elements present in DLL.\n");
        printf("10.Reversing of DLL.\n");
        printf("Enter your choice:\n");
        scanf("%d",&choice);
        switch(choice)
        {
            case 1:
                    create();
                    break;
            case 2:
                    display();
                    break;
            case 3:
                    insert_at_beg();
                    break;
            case 4:
                    insert_at_end();
                    break;
            case 5:
                    insert_at_pos();
                    break;
            case 6:
                    delete_at_beg();
                    break;
            case 7:
                    delete_at_end();
                    break;
            case 8:
                    delete_at_pos();
                    break;
            case 9:
                    count();
                    break;
            case 10:
                    reverse();
                    break;
        }
    }
}
