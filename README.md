# merge_twosorted_LL
#include<iostream>
using namespace std;


class Node
{
    public:
    int data;
    Node* next;
    Node(int data)
    {
        this->data=data;
        next=NULL;
    }
};
Node* input()
{
    int data;
    cin>>data;
    Node* head=NULL;
    Node* tail=NULL;
    while(data!=-1)
    {
        Node* newNode=new Node(data);
        if(head==NULL)
        {
            head=newNode;
            tail=newNode;
        }
        else
        {
            tail->next=newNode;
            tail=tail->next;
        }
        cin>>data;
    }
    return head;
}
void print(Node* head)
{
    Node* temp=head;
    while(temp!=NULL)
    {
        cout<<temp->data<<" ";
        temp=temp->next;
    }
}

Node* merge_two_linkedlist(Node* h1,Node* h2)
{
    Node* head=NULL;
    Node* tail=NULL;
     if(h1->data<=h2->data)
        {
            head=h1;
            tail=h1;
        
            h1=h1->next;
             
            
        }
     while(h1!=NULL&&h2!=NULL)
     {
        if(h1->data>=h2->data)
        {
            tail->next=h2;
            tail=tail->next;
            h2=h2->next;
           
        }
        else
        {
            tail->next=h1;
            tail=tail->next;
            h1=h1->next;
        }
            
        }
     
     while(h1!=NULL)
     {
        tail->next=h1;
        tail=tail->next;
        h1=h1->next;
     }
     while(h2!=NULL)
     {
          tail->next=h2;
            tail=tail->next;
            h2=h2->next;
     }

     return head;

}


int main()
{
    Node* h1=input();
    Node* h2=input();
    Node* h3=merge_two_linkedlist(h1,h2);

    print(h3);
}
