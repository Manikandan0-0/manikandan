/* 8.c DLL */
#include <stdio.h>
#include <stdlib.h>
typedef struct NODE Node;
struct NODE
{
    char ssn[20];
    char name[20];
    char dept[20];
    char desig[20];
    char salary[10];
    char phone[12];
    Node *next;
    Node *prev;
};

void get(char *prompt, char *s)
{
    printf("Enter %s:", prompt);
    scanf("%s", s);
}

Node *start = NULL;

Node *info()
{
    Node *s;
    s = malloc(sizeof(Node));
    printf("Enter s info:");
    get("SSN", s->ssn);
    get("Name", s->name);
    get("Dept", s->dept);
    get("Designation", s->desig);
    get("Salary", s->salary);
    get("Phone", s->phone);
    s->next = NULL;
    return(s);
}

void insert_front()
{
    Node *student;
    student = info();
    if(start == NULL)
    {
        student->next = NULL;
        student->prev = NULL;
        start = student;
        return;
    }
    student->next = start;
    student->prev = NULL;
    start->prev = student;
    start = student;
}

void insert_end()
{
    Node *p, *student;
    student = info();
    if(start == NULL)
    {
        start = student;
        student->prev = NULL;
        return;
    }
    p = start;
    while(p->next != NULL)
    {
        p = p->next;
    }
    p->next = student;
    student->prev = p;
}

void delete_front()
{
    Node *p;
    if(start == NULL)
    {
        printf("The DLL list is empty. \n");
        return;
    }
