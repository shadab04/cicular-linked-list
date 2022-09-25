  #include<stdio.h>
#include<stdlib.h>
struct node
{
    int data;
    struct node *next;
};
struct node *head;
void insertbeg();
void insertend();
void insertloc();
void deletebeg();
void deleteend();
void deleteloc();
void display();
void search();
void main ()
{
    int choice =0;
    while(choice != 7)
    {
        printf("\nEnter your choice?\n");
        scanf("\n %d ", &choice);
        switch(choice)
        {
            case 1:
            insertbeg();
            break;
            case 2:
             insertend();
            break;
            case 3:
           deletebeg();
            break;
            case 4:
           deleteend();
            break;
            case 5:
            search();
            break;
            case 6:
            display();
            break;
            case 7:
            exit(0);
            break;
            default:
            printf("Please enter valid choice..");
        }
    }
}

void insertbeg()
{
    struct node *nn,*temp;
    int item;
    nn = (struct node*)malloc(sizeof(struct node));
    if(nn == NULL)
    {
        printf("\nOVERFLOW");
    }
    else
    {
        printf("\nEnter the node data:");
        scanf("%d",&item);
        nn -> data = item;
        if(head == NULL)
        {
            head = nn;
            nn -> next = head;
        }
        else
        {
            temp = head;
            while(temp->next != head)
                temp = temp->next;
            nn->next = head;
            temp -> next = nn;
            head = nn;
        }
        printf("\n node inserted \n");
    }

}
void insertend()
{
    struct node *nn,*temp;
    int item;
    nn = (struct node*)malloc(sizeof(struct node));
    if(nn == NULL)
    {
        printf("\nOVERFLOW\n");
    }
    else
    {
        printf("\nEnter Data?");
        scanf("%d",&item);
        nn -> data = item;
        if(head == NULL)
        {
            head = nn;
            nn -> next = head;
        }
        else
        {
            temp = head;
            while(temp -> next != head)
            {
                temp = temp -> next;
            }
            temp -> next = nn;
            nn -> next = head;
        }

        printf("\n node inserted\n");
    }

}

void deletebeg()
{
    struct node *nn;
    if(head == NULL)
    {
        printf("\n UNDERFLOW ");
    }
    else if(head->next == head)
    {
        head = NULL;
        free(head);
        printf("\n node deleted \n");
    }

    else
    {   nn = head;
        while(nn -> next != head)
            nn = nn -> next;
        nn->next = head->next;
        free(head);
        head = nn->next;
        printf("\n node deleted \n");

    }
}
void deleteend()
{
    struct node *nn, *temp;
    if(head==NULL)
    {
        printf("\n UNDERFLOW ");
    }
    else if (head ->next == head)
    {
        head = NULL;
        free(head);
        printf("\n node deleted \n");

    }
    else
    {
        nn = head;
        while(nn ->next != head)
        {
            temp = nn;
            nn = nn -> next;
        }
        temp -> next = nn -> next;
        free(nn);
        printf("\n node deleted \n");

    }
}

void search()
{
    struct node *nn;
    int item,i=0,flag=1;
    nn = head;
    if(nn == NULL)
    {
        printf("\n Empty List \n");
    }
    else
    {
        printf("\nEnter item which you want to search:\n");
        scanf("%d",&item);
        if(head ->data == item)
        {
        printf("item found at location %d",i+1);
        flag=0;
        }
        else
        {
        while (nn -> next != head)
        {
            if(nn -> data == item)
            {
                printf("item found at location %d ",i+1);
                flag=0;
                break;
            }
            else
            {
                flag=1;
            }
            i++;
            nn = nn -> next;
        }
        }
        if(flag != 0)
        {
            printf("Item not found\n");
        }
    }

}

void display()
{
    struct node * nn;
     nn = head;
    if(head == NULL)
    {
        printf("\n nothing to print ");
    }
    else
    {
        printf("\n printing values ... \n");

        while( nn -> next != head)
        {

            printf("%d\n",  nn -> data);
             nn = nn -> next;
        }
        printf("%d \n", nn -> data);
    }

}
