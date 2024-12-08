# Anyview数据结构参考代码

## 第1章

### DC01PE06

```c++
#include "allinclude.h"  //DO NOT edit this line
void Descend(int &a, int &b, int &c)  // 通过交换，令 a >= b >= c
{   // Add your code here
    int temp;
    if(a < b)
    {
        temp = b;
        b = a;
        a = temp;
    }
    if(b < c)
    {
        temp = c;
        c = b;
        b = temp;
    }
    if(a < b)
    {
        temp = b;
        b = a;
        a = temp;
    }
}
```

### DC01PE08

```c++
#include "allinclude.h"  //DO NOT edit this line
float Polynomial(int n, int a[], float x0) 
{   // Add your code here
    float rlt = 0;
    for(int i = 0; i <= n; ++i)
    {
        rlt += a[i]*pow(x0,i);
    }
    return rlt;
}
```

### DC01PE11

```c++
#include "allinclude.h"  //DO NOT edit this line
Status Fibonacci(int k, int m, int &f) { 
    // Add your code here
    if (k < 2 || m < 0)
    {
        return ERROR;
    }

    if(m < k-1)
    {
        f += 0;
    }
    else if (m == k-1)
    {
        f += 1;    
    }
    else 
    {
        for(int i = m-1; i >= m-k; --i)
        {
            Fibonacci(k,i,f);
        }
    }
    return OK;
}
```

### DC01PE18

```c++
#include "allinclude.h"  //DO NOT edit this line

int fac(int num)
{
    if (num == 1) 
    {
        return 1;
    }
    return num * fac(num-1);
}

Status Series(int a[], int n) { 
    // Add your code here
    Status flag = OK;
    if(n <= 0)
    {
        flag = ERROR;
    }
    for(int i = 1; i <= n; ++i)
    {
        int temp = fac(i) * pow(2,i);
        if (temp > MAXINT) 
        {
            flag = EOVERFLOW;
            continue;
        }
        a[i-1] = fac(i) * pow(2,i);
    }
    return flag;
}
```

### DC01PE20

```c++
#include "allinclude.h"
void printName(stuType student[], int index[], int n)
{  // Add your code here
    for(int i = 0; i < n; ++i)
    {
        for(int j = 0; j < 4; ++j)
        {
            printf("%c",student[index[i]].name[j]);
        }
        printf("\n");    
    }
}
```

### DC01PE21

```c++
#include "allinclude.h"
float highestScore(stuType *student[], int n)
/* 返回最高成绩  */
{  // Add your code here
    float maxScore = 0;
    for(int i = 0; i < n; ++i)
    {
        if(student[i]->score > maxScore)
        {
            maxScore = student[i]->score;
        }
    }
    return maxScore;
}
```

### DC01PE22

```c++
#include "allinclude.h"
void printFirstName_HighestScore(stuType *student[], int n)
{  // Add your code here
    float maxScore = 0;
    int maxScoreIndex = 0;
    for (int i = 0; i < n; ++i) 
    {
        if(student[i]->score > maxScore)
        {
            maxScore = student[i]->score;
            maxScoreIndex = i;
        }    
    }
    for(int j = 0; j < 4; ++j)
    {
        printf("%c",student[maxScoreIndex]->name[j]);
    }
    printf("\n%.2f\n",maxScore);
}
```

### DC01PE23

```c++
#include "allinclude.h"
void printLastName_HighestScore(stuType *student[], int n)
{  // Add your code here
    float maxScore = 0;
    int maxScoreIndex = 0;
    for (int i = 0; i < n; ++i) 
    {
        if(student[i]->score >= maxScore)
        {
            maxScore = student[i]->score;
            maxScoreIndex = i;
        }    
    }
    for(int j = 0; j < 4; ++j)
    {
        printf("%c",student[maxScoreIndex]->name[j]);
    }
    printf("\n%.2f\n",maxScore);
}
```

### DC01PE30

```c++
#include "allinclude.h"
StrSequence* reverseStr(StrSequence* strSeq)
/*返回一个结构体，该结构体将strSeq中的字符串逆序存放*/
{  // Add your code here
    ElemType* reverseStr = (ElemType*)malloc(strSeq->length*sizeof(char));      //中间缓冲区
    for(int i = 0, j = strSeq->length-1; i < strSeq->length; ++i,--j)
    {
        reverseStr[i] = strSeq->elem[j];
    }
    strSeq->elem = reverseStr;
    return strSeq;
}
```

### DC01PE49

```c++
#include "allinclude.h"  //DO NOT edit this line
Status CreateSequence(Sequence &S, int n, ElemType *a) { 
   if(n <= 0 || a == NULL)
   {
      return ERROR;
   }
   S.elem = (ElemType*)malloc(n*sizeof(ElemType));
   for (int i = 0; i < n; i++) 
   {
      S.elem[i] = a[i];
   }
   S.length = n;
   return OK;
}
```

### DC01PE61

```c++
#include "allinclude.h"  //DO NOT edit this line
LinkList MakeNode(ElemType x) { 
    LinkList pNode = (LinkList)malloc(sizeof(LNode));
    if (pNode) 
    {
        pNode->data = x;
        pNode->next = NULL;       
    }
    return pNode;
}
```

### DC01PE63

```c++
#include "allinclude.h"  //DO NOT edit this line
LinkList CreateLinkList(ElemType x, ElemType y) { 
    LinkList pHead = (LinkList)malloc(sizeof(LNode));
    if(pHead)
    {
        pHead->data = x;
        pHead->next = (LinkList)malloc(sizeof(LNode));
        if(pHead->next)
        {
            pHead->next->data = y;
            pHead->next->next = NULL;
        }
        else 
        {
            return NULL;
        }
    }
    return pHead;
}
```

### DC01PE65

```c++
#include "allinclude.h"  //DO NOT edit this line
LinkList CreateOrdLList(ElemType x, ElemType y) { 
    // Add your code here
    LinkList pHead = (LinkList)malloc(sizeof(LNode));
    if(pHead)
    {
        pHead->data = x<y?x:y;
        pHead->next = (LinkList)malloc(sizeof(LNode));
        if(pHead->next)
        {
            pHead->next->data = x>y?x:y;;
            pHead->next->next = NULL;
        }
        else 
        {
            return NULL;
        }
    }
    return pHead;
}
```

## 第2章

### DC02PE03

```c++
#include "allinclude.h"  //DO NOT edit this line
Status StackEmpty_Sq(SqStack S) { 
    if(S.top == 0)
    {
        return TRUE;
    }
    return FALSE;
}
```

### DC02PE05

```c++
#include "allinclude.h"  //DO NOT edit this line
Status GetTop_Sq(SqStack S, ElemType &e) 
{// Add your code here
    if(S.top == 0)
    {
        return ERROR;
    }
    e = S.elem[--S.top];
    return OK;
}
```

### DC02PE07

```c++
#include "allinclude.h"  //DO NOT edit this line
Status Pop_Sq(SqStack &S, ElemType &e) { 
    if(S.top == 0)
    {
        return ERROR;
    }
    e = S.elem[--S.top];
    return OK;
}
```

### DC02PE11

```c++
#include "allinclude.h"  //DO NOT edit this line
Status InitStack_Sq2(SqStack2 &S, int size, int inc) { 
    if(size <= 0 || inc <= 0)
    {
        return ERROR;
    }
    S.elem = (ElemType*)malloc(size*sizeof(ElemType));
    S.top = S.elem;
    S.size = size;
    S.increment = inc;
    return OK;
}
```

### DC02PE13

```c++
#include "allinclude.h"  //DO NOT edit this line
Status StackEmpty_Sq2(SqStack2 S) { 
    if(S.top == S.elem)
    {
        return TRUE;
    }
    return FALSE;
}
```

### DC02PE15

```c++
#include "allinclude.h"  //DO NOT edit this line
Status Push_Sq2(SqStack2 &S, ElemType e) { 
    if(S.top == S.elem+S.size)
    {
        S.elem = (ElemType*)realloc(S.elem,S.size+S.increment);
        if(!S.elem)
        {
            return ERROR;
        }
        S.top = S.elem+S.size;
    }
    *S.top = e;
    S.top++;
    return OK;
}
```

### DC02PE17

```c++
#include "allinclude.h"  //DO NOT edit this line
Status Pop_Sq2(SqStack2 &S, ElemType &e) { 
    if(S.top == S.elem)
    {
        return ERROR;
    }
    e = *(--S.top);
    return OK;
}
```

### DC02PE19

```c++
#include "allinclude.h"  //DO NOT edit this line
Status CopyStack_Sq(SqStack S1, SqStack &S2) { 
    if(StackEmpty_Sq(S1))
    {
        S2 = S1;
        return TRUE;
    }

    SqStack tempSq;
    Status flag1,flag2;
    flag1 = InitStack_Sq(tempSq, S1.size, S1.increment);
    flag2 = InitStack_Sq(S2, S1.size, S1.increment);
    if(!(flag1 && flag2))
    {
        return ERROR;
    }
    while(S1.top != 0)
    {
        tempSq.elem[tempSq.top++] = S1.elem[--S1.top]; 
    }
    while(tempSq.top != 0) 
    {
        S2.elem[S2.top++] = tempSq.elem[--tempSq.top];
    }
    return TRUE;
}
```

### DC02PE20

```c++
#include "allinclude.h"
void Conversion(int N, int rd)
{  // Add your code here
    SqStack tempStack;
    ElemType temp;
    InitStack_Sq(tempStack, MAXSIZE, INCREMENT);

    while(N >= rd)
    {
        temp = N % rd;
        N /= rd;
        Push_Sq(tempStack, temp);
    }
    Push_Sq(tempStack,N);
    while(Pop_Sq(tempStack, temp))
    {
        printf("%d",temp);
    }
    DestroyStack_Sq(tempStack);
}
```

### DC02PE21

```c++
#include "allinclude.h"
Status matchBracketSequence(char* exp, int n)
{  // Add your code here
    if(n & 1 == 1)
    {
        return FALSE;
    }
    Status flag = TRUE;
    SqStack bufStack;
    ElemType temp;
    InitStack_Sq(bufStack, MAXSIZE, INCREMENT);
    for(int i = 0; i < n; ++i)
    {
        if(exp[i] == '{' || exp[i] == '[' || exp[i] == '(')
        {
            Push_Sq(bufStack, exp[i]);
            continue;
        }
        if(!Pop_Sq(bufStack, temp))
        {
            return FALSE;
        }
        if((temp == '{' && exp[i] != '}') || (temp == '[' && exp[i] != ']') || (temp == '(' && exp[i] != ')'))
        {
            return FALSE;
        }
    }
    if(!StackEmpty_Sq(bufStack))
    {
        flag = FALSE;
    }
    DestroyStack_Sq(bufStack);
    return flag;
}
```

### DC02PE23

```c++
#include "allinclude.h"  //DO NOT edit this line
int QueueLength_Sq(SqQueue Q) { 
    int queueLength = 0;
    while (Q.front != Q.rear) {
        Q.front = (Q.front+1)%Q.maxSize;
        ++queueLength;
    }
    return queueLength;
}
```

### DC02PE25

```c++
#include "allinclude.h"  //DO NOT edit this line
Status EnCQueue(CTagQueue &Q, ElemType x) { 
    if(Q.rear == Q.front && Q.tag == 1)
    {
        return ERROR;    
    }
    Q.elem[Q.rear] = x;
    Q.rear = (++Q.rear)%MAXQSIZE;
    if(Q.rear == Q.front)
    {
        Q.tag = 1;
    }
    return OK;
}

Status DeCQueue(CTagQueue &Q, ElemType &x){
   // Add your code here
    if(Q.rear == Q.front && Q.tag == 0)
    {
        return ERROR;    
    }
    x = Q.elem[Q.front];
    Q.front = (++Q.front)%MAXQSIZE;
    if(Q.front == Q.rear)
    {
        Q.tag = 0;
    }
    return OK;
}
```

### DC02PE27

```c++
#include "allinclude.h"  //DO NOT edit this line
Status EnCQueue(CLenQueue &Q, ElemType x) { 
    // Add your code here
    if (Q.length == MAXQSIZE) 
    {
        return ERROR;    
    }
    Q.elem[(++Q.rear) % MAXQSIZE] = x;
    Q.length++;
    return OK;
}

Status DeCQueue(CLenQueue &Q, ElemType &x){
    // Add your code here
    if(Q.length == 0)
    {
        return ERROR;
    }
    if (Q.rear >= Q.length) {
        x = Q.elem[Q.rear - Q.length + 1];
    }
    else {
        x = Q.elem[(Q.rear + (MAXQSIZE-Q.length)+1) % MAXQSIZE];
    }
    Q.length--;
    return OK;
}
```

### DC02PE32

```c++
#include "allinclude.h"  //DO NOT edit this line

Status InitSqQueue(SqQueue* queue, int size)
{
    if (queue) 
    {
        queue->maxSize = size;
        queue->base = (ElemType*)malloc(size*sizeof(ElemType));
        queue->front = 0;
        queue->rear = 0;
        return OK;
    }
    return ERROR;
}

long Fib(int k, int n) { 
    // Add your code here
    long rlt = 0;
    int temp = 0;
    SqQueue fibQueue;
    InitSqQueue(&fibQueue, n+1);
    for(int i = 0; i < n+1; ++i)
    {
        if(i < k-1) 
        {
            fibQueue.base[fibQueue.rear++] = 0; 
            fibQueue.rear %= fibQueue.maxSize;
        }
        else if (i == k-1) 
        {
            fibQueue.base[fibQueue.rear++] = 1; 
            fibQueue.rear %= fibQueue.maxSize;
        }
        else 
        {
            temp = 0;
            for(int j = i-k; j < i; ++j)
            {
                temp += fibQueue.base[j]; 
            }    
            fibQueue.base[fibQueue.rear++] = temp;
            fibQueue.rear %= fibQueue.maxSize;
        }
    }
    rlt = fibQueue.base[n];
    return rlt;
}
```

### DC02PE33

```c++
#include "allinclude.h"  //DO NOT edit this line
char Compare(SqList A, SqList B) 
{ // Add your code here
    if (A.length == 0 && B.length != 0) {
        return '<';
    }
    else if (B.length == 0 && A.length != 0) {
        return '>';
    }
    else if (A.length == 0 && B.length == 0) {
        return '=';
    }
    else {
        int i;
        for (i = 0; i < A.length; ++i) {
            if (i == B.length) {
                return '>';
            }
            if(A.elem[i] == B.elem[i])
            {
                continue;
            }
            else if (A.elem[i] > B.elem[i]) {
                return '>';
            }
            else {
                return '<';
            }
        }
        if (i < B.length) {
            return '<';
        }
        return '=';
    }
}
```

### DC02PE35

```c++
#include "allinclude.h"  //DO NOT edit this line
void Inverse(SqList &L) 
{ // Add your code here
    ElemType temp;
    for (int i = 0; i < L.length/2; ++i) {
        temp = L.elem[i];
        L.elem[i] = L.elem[L.length-1-i];
        L.elem[L.length-1-i] = temp;
    }
}
```

### DC02PE45

```c++
#include "allinclude.h"  //DO NOT edit this line
void Union(SqList &La, List Lb)
{     // Add your code here
    for (int i = 0; i < Lb.length; i++) {
        if(Search_Sq(La,Lb.elem[i]) == -1)
        {
            Append_Sq(La, Lb.elem[i]);
        }
    }
}
```

### DC02PE53

```c++
#include "allinclude.h"  //DO NOT edit this line
Status StackEmpty_L(LStack S) 
{    // Add your code here
    if (S) {
        return FALSE;
    }
    return TRUE;
}
```

### DC02PE55

```c++
#include "allinclude.h"  //DO NOT edit this line
Status GetTop_L(LStack S, ElemType &e) 
{    // Add your code here
    if (S) {
        e = S->data;
        S = S->next;
        return OK;
    }
    return ERROR;
}
```

### DC02PE61

```c++
#include "allinclude.h"  //DO NOT edit this line
Status QueueEmpty_LQ(LQueue Q)
{    // Add your code here
    if (Q.front) {
        return FALSE;
    }
    return TRUE;
}
```

### DC02PE63

```c++
#include "allinclude.h"  //DO NOT edit this line
int QueueLength_LQ(LQueue Q) 
{   // Add your code here
    int queueLength = 0;
    if (!Q.front) {
        return queueLength;
    }
    while(Q.front != Q.rear)
    {
        queueLength++;
        Q.front = Q.front->next;
    }
    return ++queueLength;
}
```

### DC02PE68

```c++
#include "allinclude.h"  //DO NOT edit this line
Status InitCLQueue(CLQueue &rear) 
{   // Add your code here
    rear = (CLQueue)malloc(sizeof(CLQNode));
    if(!rear)
        return EOVERFLOW;
    rear->data = 0;
    rear->next = rear;
    return OK;
} 

Status EnCLQueue(CLQueue &rear, ElemType x)
{   // Add your code here
    if(rear)
    {       
        CLQueue tempCLQueue;
        tempCLQueue = (CLQueue)malloc(sizeof(CLQNode));
        if(!tempCLQueue)
        {
            return EOVERFLOW;
        }
        tempCLQueue->next = rear->next;
        tempCLQueue->data = x;
        rear->next = tempCLQueue;
        rear = rear->next;
        return OK;
    }
    return ERROR;
}

Status DeCLQueue(CLQueue &rear, ElemType &x)
{    // Add your code here
    if (rear == rear->next) {
        return ERROR;
    }
    if(rear)
    {
        CLQueue frontCLQueue = rear->next->next;
        x = frontCLQueue->data;
        rear->next->next = frontCLQueue->next;
        free(frontCLQueue);
        frontCLQueue = NULL;
        return OK;
    }
    return ERROR;
}
```

### DC02PE71

```c++
#include "allinclude.h"  //DO NOT edit this line
Status ListEmpty_L(LinkList L) 
{    // Add your code here
    if(!L)
    {
        return ERROR;
    }
    if(L->next)
    {
        return FALSE;
    }
    return TRUE;
}
```

### DC02PE73

```c++
#include "allinclude.h"  //DO NOT edit this line
Status DestroyList_L(LinkList &L) 
{    // Add your code here
    LinkList temp = NULL;
    while(L)
    {
        temp = L;
        L = L->next;
        free(temp);
    }
    return OK;
}
```

### DC02PE75

```c++
#include "allinclude.h"  //DO NOT edit this line
Status ClearList_L(LinkList &L)
{    // Add your code here
    if(!L)
    {
        return ERROR;
    }
    while(L->next)
    {
        L->data = NULL;
        L = L->next;
    }
    return OK;
}
```

### DC02PE77

```c++
#include "allinclude.h"  //DO NOT edit this line
int ListLength_L(LinkList L) 
{   // Add your code here
    int length = 0;
    if(!L)
    {
        return -1;
    }
    while(L)
    {
        ++length;
        L = L->next;
    }
    return length-1;
}
```

### DC02PE82

```c++
#include "allinclude.h"  //DO NOT edit this line
Status Insert_L(LinkList L, int i, ElemType e) 
{   // Add your code here
    if (!L || i <= 0) {
        return ERROR;
    }
    LinkList p = (LinkList)malloc(sizeof(LNode));
    LinkList q = L->next;
    while (i-- != 1) {
        L = L->next;
        if(q)
        {
            q = q->next;
        }
        if(!L)
        {
            return ERROR;
        }
    }
    p->data = e;
    if(q)
    {
        p->next = q;
        L->next = p;
    }
    else {
        L->next = p;
        p->next = NULL;
    }
    return OK;
}
```

### DC02PE84

```c++
#include "allinclude.h"  //DO NOT edit this line
Status Delete_L(LinkList L, int i, ElemType &e) 
{   // Add your code here
    if (i < 1 || !L) {
        return ERROR;
    }
    LinkList p = L;
    LinkList q = L->next;
    for(; i-- != 1; p = q, q = q->next)
    {
        if(!q)
        {
            return ERROR;
        }
    }
    if(!q)
        return ERROR;
    e = q->data;
    p->next = q->next;
    free(q);
    q = NULL;
    return OK;
}
```

### DC02PE86

```c++
#include "allinclude.h"  //DO NOT edit this line
Status Split_L(LinkList L, LinkList &Li, int i)
{   // Add your code here
    Li = NULL;
    if(i < 1 || !L)
    {
        return ERROR;
    }
    LinkList p = L;
    LinkList q = L->next;
    for(;i-- != 1; p = q, q = q->next)
    {
        if(!q)
        {
            return ERROR;
        }
    }
    if(!q)
    {
        return ERROR;
    }
    p->next = NULL;
    Li = (LinkList)malloc(sizeof(LNode));
    Li->next = q;
    return OK;
}
```

### DC02PE88

```c++
#include "allinclude.h"  //DO NOT edit this line
Status Cut_L(LinkList L, int i)
{   // Add your code here
    if(i < 1 || !L)
    {
        return ERROR;
    }
    LinkList p = L;
    LinkList q = L->next;
    for(;i-- != 1; p = q, q = q->next)
    {
        if(!q)
        {
            return ERROR;
        }
    }
    if(!q)
    {
        return ERROR;
    }
    p->next = NULL;
    while(q)
    {
        p = q;
        q = q->next;
        free(p);
    }
    p = NULL;
    return OK;
}
```

### DC02PE90

```c++
#include "allinclude.h"  //DO NOT edit this line
Status DeleteX_L(LinkList L, ElemType x)  
{   // Add your code here
    if(!L)
    {
        return ERROR;
    }
    int deleteCount = 0;
    LinkList p = L;
    LinkList q = L->next;
    LinkList temp = NULL;
    while(q)
    {
        if(q->data == x)
        {
            ++deleteCount;
            p->next = q->next;
            temp = q;
            q = q->next;
            free(temp);
            continue;
        }
        else 
        {
            p = q;
            q = q->next;
        }
    }
    temp = NULL;
    return deleteCount;
}
```

### DC02PE91

```c++
#include "allinclude.h"  //DO NOT edit this line
Status DeleteSome_L(LinkList L, ElemType x)  
{   // Add your code here
    if(!L)
    {
        return ERROR;
    }
    int deleteCount = 0;
    LinkList p = L;
    LinkList q = L->next;
    LinkList temp = NULL;
    while(q)
    {
        if(q->data < x)
        {
            ++deleteCount;
            p->next = q->next;
            temp = q;
            q = q->next;
            free(temp);
            continue;
        }
        else 
        {
            p = q;
            q = q->next;
        }
    }
    temp = NULL;
    return deleteCount;
}
```

### DC02PE93

```c++
#include "allinclude.h"  //DO NOT edit this line
DuLinkList delDuplicateDuLNodes(DuLinkList L)
{   // Add your code here
    if(!L)
    {
        return L;
    }
    DuLinkList p = L->next;
    DuLinkList q = NULL;
    DuLinkList temp = NULL;
    while(p)
    {
        q = p->next;
        while(q)
        {
            if (q->data == p->data) {
                temp = q;
                if(q->next)
                {
                    q->prior->next = q->next;
                    q->next->prior = q->prior;
                }
                else 
                {
                    q->prior->next = NULL;    
                }
                q = q->next;
                free(temp);
            }
            else {
                q = q->next;
            }
        }
        p = p->next;
    }
    temp = NULL;
    return L;
}
```

### DC02PE94

```c++
#include "allinclude.h"  //DO NOT edit this line
void reverseDuLinkList(DuLinkList L)
{   // Add your code here
    if(!L || !L->next)
    {
        return;
    }

    DuLinkList p = L->next, q = NULL;
    L->next = NULL;
    while(p)
    {
        //q为下一个要插入到L节点后的节点
        q = p->next;

        //将p节点插入到L节点直接后继
        p->prior = L;
        p->next = L->next; 
        if(L->next)
        {
            L->next->prior = p;
        }
        L->next = p;

        p = q;
    }
}
```

### DC02PE95

```c++
#include "allinclude.h"  //DO NOT edit this line
void reverseDuCirLinkList(DuCirLinkList L)
{   // Add your code here
    if(!L || !L->next)
    {
        return;
    }

    //暂时保存头节点和首末节点的循环关系
    DuLinkList p = L->next, q = NULL, lastFrontP = L->next;
    //将头节点与所以数据节点暂时切断链接
    L->next = NULL;
    L->prior->next = NULL;
    while(p)
    {
        //q为下一个要插入到L节点后的节点
        q = p->next;

        //将p节点插入到L节点直接后继
        p->prior = L;
        p->next = L->next; 
        if(L->next)
        {
            L->next->prior = p;
        }
        L->next = p;

        p = q;
    }
    L->prior = lastFrontP;
    lastFrontP->next = L;
}
```

### DC02PE97

```c++
#include "allinclude.h"  //DO NOT edit this line
void InterleavedTravelDuCirLinkList(DuCirLinkList L, DuLNode* p)
{   // Add your code here
    DuCirLinkList f = p->next, r = p->prior;
    if (f == p) {
        return;
    }
    if (f == r) {
        if(p != L)
        {
            printf("%c",p->data); 
        }
        else {
            printf("%c",f->data); 
        }
    }
    else {
        while(1) {
            if(f == r)
                break;
            if(f == L || f == p)        //对遍历时出现的特殊情况处理
                f = f->next; 
                if(f == r)
                    break;
            printf("%c",f->data);   
            f = f->next; 

            if(r == f)
                break;
            if(r == L || r == p)
                r = r->prior; 
                if(f == r)
                    break;
            printf("%c",r->data);   
            r = r->prior;
        }
        if(r != L)                      //如果重合遍历位置不是头结点，则输出
        {
            printf("%c",r->data);  
        }
        if(p != L)                      //如果起始位置不是头结点，则输出
        {
            printf("%c",p->data); 
        }
    }
}
```

### DC02PE98

```c++
#include "allinclude.h"  //DO NOT edit this line
Status isLeagalDuCirLinkList(DuCirLinkList L)
{   // Add your code here
    //思路：根据双向循环链表定义，出现空节点一定是不合法，所以主要是做判空操作，还有前驱和后继节点判断
    if (!L) {
        return TRUE; 
    }
    DuCirLinkList p = L->next;
    if(!p)
    {
        return FALSE;
    }
    if(p == L->prior)
    {
        return TRUE;
    }
    while(p != L)
    {
        if(p->next) 
        {
            if (p->next->prior) {
                if(p->next->prior == p)
                {
                    p = p->next;
                    continue;
                }
                else {
                    return FALSE;
                }       
            }
            return FALSE;   
        }
        return FALSE;
    }
    return TRUE;
}
```

## 第3章

### DC03PE01

```c++
#include "allinclude.h"  //DO NOT edit this line
int conflictsOfInsertSort(RcdSqList* L)
{ 
    int result = 0;
    int i, j;
    for (i = 1; i < L->length; ++i)
    {
        if (L->rcd[i + 1].key < L->rcd[i].key)
        { 
            L->rcd[0] = L->rcd[i + 1];
            j = i + 1;
            do {
                j--;
                L->rcd[j + 1] = L->rcd[j];
                ++result;
            } while (L->rcd[0].key < L->rcd[j - 1].key); 
            L->rcd[j] = L->rcd[0];
        }
    }
    return result;
}
```

### DC03PE03

```c++
#include "allinclude.h"  //DO NOT edit this line
void InsertSort(RcdSqList &L)
{ // Add your code here
    int i,j;
    for (i = 1; i < L.length; ++i) {
        if (L.rcd[i+1].key < L.rcd[i].key) {
            L.rcd[L.length+1].key = L.rcd[i+1].key;
            j = i+1;
            do
            {
                j--;
                L.rcd[j+1].key = L.rcd[j].key;
            }while(L.rcd[L.length+1].key < L.rcd[j-1].key); 
            L.rcd[j].key = L.rcd[L.length+1].key;
        }
    }
}
```

### DC03PE06

```c++
#include "allinclude.h"  //DO NOT edit this line
void BubbleSort(RcdSqList2 &L) 
{ // Add your code here
    int change = L.length,temp_change = L.length;
    int j;
    for (int i = 1; i <= L.length; i++) {
        for (j = 1; j < change; j++) {
            if(GT(L.rcd[j],L.rcd[j+1]))
            {
                Swap(L.rcd[j],L.rcd[j+1]);
                temp_change = j;
            }
        }
        if(change == temp_change)
        {
            break;
        }
        change = temp_change;
    }

}
```

### DC03PE23

```c++
#include "allinclude.h"  //DO NOT edit this line
void CountSort(RcdSqList2 &L)  
{ // Add your code here
    int c[MAXSIZE+1] = {0};
    KeyType a[MAXSIZE+1] = {0};     //保留初始序列，辅助后期对序列进行重新排列
    for (int i = 1; i <= L.length; ++i) {
        a[i] = L.rcd[i].key;
    }
    for (int i = 1; i <= L.length; ++i) {
        for(int j = 1; j <= L.length; ++j)
        {
            if (L.rcd[j].key < a[i]) {
                ++c[i];
            }
        }
    }
    for (int i = 0; i < L.length; ++i) {
        for(int j = 1; j <= L.length; ++j)
        {
            if (c[j] == i) {
                L.rcd[i+1].key = a[j];
                break;
            }
        }
    }
}
```

## 第4章

### DC04PE04

```c++
#include "allinclude.h"  //DO NOT edit this line
void PrintKeys(HashTable ht, void(*print)(StrKeyType)){
/* 请调用形参中的print函数输出关键字 */
    for (char letter = 'A'; letter <= 'Z'; letter++) {
        int i = (letter-'A')%ht.size;
        while(ht.rcd[i].tag != 0)       //没到空，就线性往下搜索
        {
            if (ht.rcd[i].tag == 1 && ht.rcd[i].key[0] == letter) { //必须为有效位且第一位是该字母才输出
                print(ht.rcd[i].key);
            }
            i = (i+1)%ht.size;
        }
    }
}

```

### DC04PE15

```c++
#include "allinclude.h"  //DO NOT edit this line
int BuildHashTab(ChainHashTab &H, int n, HKeyType es[])
{  // Add your code here
    H.count = 0;
    bool isRepeat = FALSE;
    for (int i = 0; i < n; i++) {
        isRepeat = FALSE;
        HLink q = H.rcd[Hash(H,es[i])];
        HLink p = (HLink)malloc(sizeof(struct HNode));
        p->data = es[i];
        p->next = NULL;
        if (H.rcd[Hash(H,es[i])]) {
            do{
                if(q->data == es[i])
                {
                    isRepeat = TRUE;
                    break;
                }
            }while (Collision(H,q));
            if(isRepeat)
            {
                free(p);
                continue;
            }
            p->next = H.rcd[Hash(H,es[i])];
            H.rcd[Hash(H,es[i])] = p;
        }
        else {
            H.rcd[Hash(H,es[i])] = p;
        }
        H.count++;
    }
}
```

### DC04PE30

```c++
#include "allinclude.h"
int countConflics(LHashTable H)
{
	int confilcsTimes = 0;
	for(int i = 0; i < H.size; ++i)
	{
		Node* p = H.rcd[i];
		if (p) {
			while (p) {
				++confilcsTimes;
				p = p->next;
			}
			--confilcsTimes;
		}
	}
	return confilcsTimes;
}
```

### DC04PE35

```c++
#include "allinclude.h"
Node* searchLHash(LHashTable H, KeyType key, int &c)
{
	Node* p = H.rcd[H.hash(key,H.size)];
	c = 0;
	if (p) {
		while (p) {
			if (p->r.key == key) {
				return p;
			}
			++c;
			p = p->next;
		}
		--c;
		return NULL;
	}
	return NULL;
}
```

## 第5章

### DC05PE04

```c++
#include "allinclude.h"  //DO NOT edit this line
int G(int m, int n) 
{  // Add your code here
    if (m == 0 && n >= 0) {
        return 0;
    }
    else if (m > 0 && n >= 0) {
        return G(m-1,2*n)+n;
    }
    else {
        return -1;
    }
}
```

### DC05PE05

```c++
#include "allinclude.h"  //DO NOT edit this line
int F(int n) 
{ // Add your code here
    if(n == 0)
    {
        return 1;
    }
    else if (n > 0) {
        return n*F(n/2);
    }
    else {
        return -1;
    }
}
```

### DC05PE06

```c++
#include "allinclude.h"  //DO NOT edit this line
float Sqrt(float A, float p, float e) 
{  // Add your code here
    if(abs(p*p-A) < e)
    {
        return p;
    }
    else{
        return Sqrt(A,(p+A/p)/2,e);
    }
}
```

### DC05PE07

```c++
#include "allinclude.h"  //DO NOT edit this line
int Akm(int m, int n) 
{  // Add your code here
    if(m < 0 || n < 0)
    {
        return -1;
    }
    else if (m != 0 && n == 0) 
    {
            return Akm(m-1,1);        

    }
    else if (m != 0 && n != 0) 
    {
        return Akm(m-1,Akm(m,n-1));
    }
    else
    {
        return n+1;
    }
}
```

### DC05PE15

```c++
#include "allinclude.h"  //DO NOT edit this line
int F(int n) 
{ // Add your code here
    int rlt = 1;
    if (n < 0) {
        rlt = -1;
    }
    else {
        for(int i = n; i > 0; i/=2)
        {
            rlt *= i;
        }
    }
    return rlt;
}
```

### DC05PE16

```c++
#include "allinclude.h"  //DO NOT edit this line
float Sqrt(float A, float p, float e) 
{  // Add your code here
    while (abs(p*p-A) >= e) {
        p = (p+A/p)/2;
    }
    return p;
}
```

### DC05PE20

```c++
#include "allinclude.h"  //DO NOT edit this line
void ChangeColor(GTYPE g, int m, int n, char c, int i0, int j0) 
{  // Add your code here
    // static char k;   ???  why Not ???
    // if(i0 <= 0 || j0 <= 0 || i0 >= m+1 || j0 >= n+1 || g[i0][j0] != k)
    // {
    //     return;
    // }
    // else {
    //     g[i0][j0] = c;
    //     ChangeColor(g,m,n,c,i0+1,j0);
    //     ChangeColor(g,m,n,c,i0-1,j0);
    //     ChangeColor(g,m,n,c,i0,j0+1);
    //     ChangeColor(g,m,n,c,i0,j0-1);
    // }
    
    if(i0==0 || j0==0 || m<1 || n<1) 
    {
        return;
    }
    char k = g[i0][j0];
    int x[4] = {-1,0,1,0};
    int y[4] = {0,1,0,-1};
    for(int i=0;i<4;i++)
    {
        if(((i0+x[i] > 0 and i0+x[i] <= m) && (j0+y[i] > 0 and j0+y[i] <= n)) && g[i0+x[i]][j0+y[i]]==k)
        {
            ChangeColor(g,m,n,c,i0+x[i],j0+y[i]);
        }
        else 
        {
             g[i0][j0]=c; 
        }
    }
}
```

### DC05PE26

```c++
#include "allinclude.h"  //DO NOT edit this line
int GListLength(GList L) 
{   // Add your code here
  int GListLength = 0;
  if (L) {
    GListLength++;
    GLNode* p = L->un.ptr.tp;
    while (p) {
      GListLength++;
      p = p->un.ptr.tp;
    }
  }
  return GListLength;
}
```

### DC05PE30

```c++
#include "allinclude.h"  //DO NOT edit this line
int GListDepth(GList ls) 
{ // Add your code here
    if (!ls) {
        return 1;
    }
    else if (ls->tag == ATOM) {
        return 0;
    }
    else {
        int depth1,depth2;
        depth1 = GListDepth(ls->un.ptr.hp) + 1;
        depth2 = GListDepth(ls->un.ptr.tp);
        return depth1 > depth2 ? depth1 : depth2;
    }
}
```

### DC05PE32

```c++
#include "allinclude.h"  //DO NOT edit this line
Status Equal(GList A, GList B) 
{  // Add your code here
    if (A != NULL && B != NULL) {
        if (A->tag == LIST && B->tag == ATOM || A->tag == ATOM && B->tag == LIST) {
            return FALSE;
        }
        else if (A->tag == LIST && B->tag == LIST) {
            return (Equal(A->un.ptr.hp,B->un.ptr.hp) && Equal(A->un.ptr.tp,B->un.ptr.tp));
        }
        else if (A->tag == ATOM && B->tag == ATOM) {
            if (A->un.atom == B->un.atom) {
                return TRUE;
            }
            else {
                return FALSE;
            }
        }
    }
    else {
        if (A == NULL && B == NULL) {
            return TRUE;
        }
        else {
            return FALSE;
        }
    }
}
```

### DC05PE33

```c++
#include "allinclude.h"  //DO NOT edit this line
void OutAtom(GList A, int layer, void(*Out2)(char, int)) 
{ // Add your code here
    if(!A)
    {
        return;
    }
    else
    {
        if(A->tag == ATOM)    
        {
            Out2(A->uoon.atom, layer);
        }
        else 
        {
            OutAtom(A->un.ptr.hp,layer+1,Out2);
            OutAtom(A->un.ptr.tp,layer,Out2);  
        }
    }
}
```

## 第6章

### DC06PE01

```c++
#include "allinclude.h"
int commonAncestor(SqBiTree T, int i, int j) 
{  // Add your code here
  if (i < 1 || j < 1 || i > T.lastIndex || j > T.lastIndex) {
    return 0;
  }
  int tempParent_I = i/2;
  while(tempParent_I)
  {
    int tempJ = j;
    while(tempJ > tempParent_I)
    {
      tempJ /= 2;
      if(tempJ == tempParent_I)
      {
        return tempParent_I;
      }
    }
    tempParent_I /= 2;
  }
  return 0;
}
```

### DC06PE02

```c++
#include "allinclude.h"
Status is_Desendant(SqBiTree T, int u, int v)  
{  // Add your code here
    if (u < 1 || v < 1 || u > T.lastIndex || v > T.lastIndex) {
        return FALSE;
    }
    while(v > u)
    {
        v /= 2;
        if (v == u) {
            return TRUE;
        }
    }
    return FALSE;
}
```

### DC06PE06

```c++
#include "allinclude.h"  //DO NOT edit this line
Status Similar(BiTree T1, BiTree T2) 
{   // Add your code here
    if(!T1 && !T2)
    {
        return TRUE;
    }
    else if(!T1 || !T2)
    {
        return FALSE;
    }
    else 
    {
        return Similar(T1->lchild,T2->lchild) && Similar(T1->rchild,T2->rchild);
    }
}
```

### DC06PE11

```c++
#include "allinclude.h"  //DO NOT edit this line

int getTreeNodeNum(BiTree T)
{
    return T ? (1+getTreeNodeNum(T->lchild)+getTreeNodeNum(T->rchild)):0;
}

TElemType PreOrderK(BiTree T, int k) 
{   // Add your code here
    if(!T || k < 1)
    {
        return '#';
    }
    int count = getTreeNodeNum(T->lchild);
    if(k == 1)
    {
        return T->data;
    }
    return count >= k-1 ? PreOrderK(T->lchild,k-1): PreOrderK(T->rchild, k-1-count);
}
```

### DC06PE12

```c++
#include "allinclude.h"  //DO NOT edit this line
int Leaves(BiTree T) 
{   // Add your code here
    if(!T)
    {
        return 0;
    }
    if(!T->lchild && !T->rchild)
    {
        return 1;
    }
    return Leaves(T->lchild)+Leaves(T->rchild);
}
```

### DC06PE21

```c++
#include "allinclude.h"  //DO NOT edit this line
void PreOrder(BiTree T, Status (*visit)(TElemType))
{   // Add your code here
    if(!T)
    {
        return ;
    }
    Stack S;
    InitStack(S);
    BiTree p;
    Push(S,T);
    while(!StackEmpty(S))
    {
        Pop(S,p);
        visit(p->data);
        if(p->rchild != NULL)
        {
            Push(S,p->rchild);
        }
        if(p->lchild != NULL)
        {
            Push(S,p->lchild);
        }
    }
}
```

### DC06PE23

```c++
#include "allinclude.h"  //DO NOT edit this line
void printNoLessThanKey_InOrder(BiTree T, TElemType k) 
{  // Add your code here
    if(!T)
    {
        return;
    }
    printNoLessThanKey_InOrder(T->lchild,k);
    if (T->data >= k) {
        printKey(T->data);
    }
    printNoLessThanKey_InOrder(T->rchild,k);
}
```

### DC06PE27

```c++
#include "allinclude.h"  //DO NOT edit this line
void printNoLessThanKey_PreOrder(BiTree T, TElemType k) 
{  // Add your code here
    if(!T)
    {
        return;
    }
    if (T->data >= k) {
        printKey(T->data);
    }
    printNoLessThanKey_PreOrder(T->lchild,k);
    printNoLessThanKey_PreOrder(T->rchild,k);
}
```

### DC06PE29

```c++
#include "allinclude.h"  //DO NOT edit this line
void printNoLessThanKey_PostOrder(BiTree T, TElemType k) 
{  // Add your code here
    if(!T)
    {
        return;
    }
    printNoLessThanKey_PostOrder(T->lchild,k);
    printNoLessThanKey_PostOrder(T->rchild,k);
    if (T->data >= k) {
        printKey(T->data);
    }
}
```

### DC06PE30

```c++
#include "allinclude.h"
Status isIsomorphic(BiTree T1, BiTree T2)
{// Add your code here
    if (!T1 && !T2) {
        return TRUE;
    }
    else if(!(T1 || T2)){
        return FALSE;
    }

    if(T1->data != T2->data)
    {
        return FALSE;
    }
    if (!T1->lchild && !T2->lchild) {
        return isIsomorphic(T1->rchild,T2->rchild);
    }
    if (!T1->rchild && !T2->rchild) {
        return isIsomorphic(T1->lchild,T2->lchild);
    }
    if ((T1->lchild && T2->lchild) && (T1->lchild->data == T2->lchild->data)) {
        return isIsomorphic(T1->lchild,T2->lchild) && isIsomorphic(T1->rchild, T2->rchild);
    }
    else {
        return isIsomorphic(T1->lchild,T2->rchild) && isIsomorphic(T1->rchild, T2->lchild);
    }
    return TRUE;
}
```

### DC06PE31

```c++
#include "allinclude.h"
void PreOrder(BiTree bt, void (*visit)(TElemType)) 
{  // Add your code here
    if(!bt)
    {
        return ;
    }
    SqStack2 S;
    InitStack_Sq2(S);
    BiTree p;
    Push_Sq2(S,bt);
    while(!StackEmpty_Sq2(S))
    {
        Pop_Sq2(S,p);
        visit(p->data);
        if(p->rchild != NULL)
        {
            Push_Sq2(S,p->rchild);
        }
        if(p->lchild != NULL)
        {
            Push_Sq2(S,p->lchild);
        }
    }
}
```

### DC06PE32

```c++
#include "allinclude.h"
void PostOrder(BiTree bt, void (*visit)(TElemType))
/* 使用栈，非递归后序遍历二叉树bt，    */
/* 对每个结点的元素域data调用函数visit */
{    // Add your code here
    if(!bt)
    {
        return ;
    }

    SqStack2 S1;
    InitStack_Sq2(S1);
    SElemType se;
    se.tag = 0;
    se.ptr = bt;
    BiTree p = bt;
    Push_Sq2(S1,se);
    while(!StackEmpty_Sq2(S1))
    {
        Pop_Sq2(S1,se);
        p = se.ptr;
        if(se.tag == 1)     //若已经过了一次
        {
            visit(se.ptr->data);
        }
        else {
            se.tag = 1;
            Push_Sq2(S1,se);
            if(p->rchild)
            {
                se.ptr = p->rchild;
                se.tag = 0; 
                Push_Sq2(S1,se);
            }
            if(p->lchild)
            {
                se.ptr = p->lchild;
                se.tag = 0;
                Push_Sq2(S1,se);
            }
        }
    }
}
```

### DC06PE33

```c++
#include "allinclude.h"  //DO NOT edit this line
void ExchangeSubTree(BiTree &T)
{   // Add your code here
    if (!T) {
        return ;
    }
    BiTree temp = T->rchild;
    T->rchild = T->lchild;
    T->lchild = temp; 

    ExchangeSubTree(T->lchild);
    ExchangeSubTree(T->rchild);
}
```

### DC06PE34

```c++
#include "allinclude.h"
void PostOrder(TriTree bt, void (*visit)(TElemType))
/* 不使用栈，非递归后序遍历二叉树bt，  */
/* 对每个结点的元素域data调用函数visit */
{  // Add your code here
    if(!bt)
    {
        return ;
    }
    TriTree p = bt;
    while(p)
    {
        if(p->mark == 0)
        {
            p->mark = 1;
            if(p->lchild)
            {
                p = p->lchild;
            }
        }
        else if (p->mark == 1) {
            p->mark = 2;
            if(p->rchild)
            {
                p = p->rchild;
            }
        }
        else if (p->mark == 2) {
            visit(p->data);
            p = p->parent;
        }
    }
}
```

### DC06PE35

```c++
#include "allinclude.h"
void InOrder(TriTree PT, void (*visit)(TElemType))
/* 不使用栈，非递归中序遍历二叉树bt，  */
/* 对每个结点的元素域data调用函数visit */
{  // Add your code here
    if(!PT)
    {
        return ;
    }
    TriTree p = PT;
    while(p)
    {
        if(p->mark == 0)
        {
            p->mark = 1;
            if(p->lchild)
            {
                p = p->lchild;
            }
        }
        else if (p->mark == 1) {
            p->mark = 2;
            visit(p->data);
            if(p->rchild)
            {
                p = p->rchild;
            }           
        }
        else if (p->mark == 2) {
            p = p->parent;
        }
    }
}
```

### DC06PE36

```c++
#include "allinclude.h"

int getTreeHeight(BiTree T)
{
    if(T==NULL)
    {
        return 0;

    }
    
    int count=1; 
    
    while(T->lchild!=NULL)  
    {
        count++;
        T=T->lchild;
    } 
    
    return count; 
}

BiTNode* getLastNode(BiTree T)
/* 求完全二叉树的最后一层的最后一个结点 */
{   // Add your code here
    if(!T)
    {
        return NULL;
    }

    if(T->lchild == NULL)  
    {
        return T;
    }
    
    if(getTreeHeight(T->lchild) > getTreeHeight(T->rchild) )
    {
        return getLastNode(T->lchild);
    }
    else  
    {
        return getLastNode(T->rchild);
    }
}

```

### DC06PE37

```c++
#include "allinclude.h"  //DO NOT edit this line
TElemType findParent(BiTree T, TElemType data, BiTNode* parent)
{   //Add your code here
    if (!T || T->data == data && !parent) {
        return '\0';
    }
    if (T->lchild && T->lchild->data == data) {
        return T->data;
    }
    if (T->rchild && T->rchild->data == data) {
        return T->data;
    }
    return findParent(T->lchild,data,T)?findParent(T->lchild,data,T):findParent(T->rchild,data,T);
}
```

### DC06PE40

```c++
#include "allinclude.h"  //DO NOT edit this line
Status isBrother(BiTree T, TElemType dx, TElemType dy)
{    // Add your code here
     if (!T) {
          return FALSE;
     }
     if (T->lchild && T->rchild) {
          if (T->lchild->data == dx && T->rchild->data == dy) {
               return TRUE;
          } 
          else if (T->rchild->data == dx && T->lchild->data == dy) {
               return TRUE;
          }  
     }
     return isBrother(T->lchild,dx,dy) || isBrother(T->rchild,dx,dy);
}
```

### DC06PE43

```c++
#include "allinclude.h"  //DO NOT edit this line
void CopyBiTree(BiTree T, BiTree &TT)
{   // Add your code here
    if(!T)
    {
        return;
    }
    TT = (BiTree)malloc(sizeof(BiTNode));
    TT->data = T->data;
    TT->lchild = T->lchild;
    TT->rchild = T->rchild;

    CopyBiTree(T->lchild,TT->lchild);
    CopyBiTree(T->rchild,TT->rchild);
}
```

### DC06PE44

```c++
#include "allinclude.h"
int Depthx(BiTree T, TElemType x)
{  // Add your code here
    if(!T)
    {
        return 0;
    }

    int deepth1,deepth2;  
    if(T->data==x)  
    {
        
        if(T->lchild==NULL)
            deepth1=0;
        else  
        {
            deepth1 = Depthx(T->lchild,T->lchild->data);
        }
        
        if(T->rchild==NULL)
            deepth2=0;
        else
        {
            deepth2 = Depthx(T->rchild,T->rchild->data);
        }
        
        return 1 + (deepth1>deepth2?deepth1:deepth2);
    }
    else
    {
        deepth1=Depthx(T->lchild,x);
        deepth2=Depthx(T->rchild,x);
        return  deepth1>deepth2?deepth1:deepth2;
    }
}
```

### DC06PE45

```c++
#include "allinclude.h"
void ReleaseX(BiTree &bt, char x)
{  // Add your code here
    if(!bt)
    {
        return;
    }
    if(bt->data == x)
    {
        if (bt->lchild) {
            ReleaseX(bt->lchild,bt->lchild->data);
        }
        if (bt->rchild) {
            ReleaseX(bt->rchild,bt->rchild->data);     
        }
        // if(!bt->lchild && !bt->rchild)
        // {
        free(bt);
        bt = NULL;
        //}
    }
    else 
    {
        ReleaseX(bt->lchild,x);
        ReleaseX(bt->rchild,x);  
    }
}

```

### DC06PE46

```c++
#include "allinclude.h"
void CopyBiTree(BiTree T, BiTree &TT)
{  // Add your code here
    if(!T)
        return;
    TT=(BiTree)malloc(sizeof(BiTNode));
    TT->data = T->data;
    TT->lchild = TT->rchild = NULL;
    LQueue Q_T,Q_TT;
    BiTree temp=TT;

    InitQueue_LQ(Q_T);
    InitQueue_LQ(Q_TT);
    EnQueue_LQ(Q_T,T);
    EnQueue_LQ(Q_TT,temp);
    
    while(QueueEmpty_LQ(Q_T)!=TRUE)
    {
        DeQueue_LQ(Q_T,T);
        DeQueue_LQ(Q_TT,temp);  
        
        if(T->lchild != NULL)
        {
            temp->lchild = (BiTree)malloc(sizeof(BiTNode));
            temp->lchild->data = T->lchild->data;
            temp->lchild->lchild = temp->lchild->rchild = NULL;
            EnQueue_LQ(Q_T,T->lchild);
            EnQueue_LQ(Q_TT,temp->lchild);
        }
        
        if(T->rchild != NULL)
        {
            temp->rchild = (BiTree)malloc(sizeof(BiTNode));
            temp->rchild->data = T->rchild->data;
            temp->rchild->lchild = temp->rchild->rchild = NULL; 
            EnQueue_LQ(Q_T,T->rchild);
            EnQueue_LQ(Q_TT,temp->rchild);
        }
        
    }
}
```

### DC06PE47

```c++
#include "allinclude.h"
void LevelOrder(BiTree bt, char *ss)
{  // Add your code here
    if(!bt)
    {
        return ;
    }
    char* ss_temp = ss;
    BiTree temp = NULL;
    LQueue Q1;
    InitQueue_LQ(Q1);

    *ss_temp++ = bt->data;
    EnQueue_LQ(Q1,bt);

    while (DeQueue_LQ(Q1,temp)) {
        if(temp->lchild != NULL)
        {
            *ss_temp++ = temp->lchild->data;
            EnQueue_LQ(Q1,temp->lchild);
        }
        if(temp->rchild != NULL)
        {
            *ss_temp++ = temp->rchild->data;
            EnQueue_LQ(Q1,temp->rchild);            
        }
    }
    *ss_temp = '\0';
}
```

### DC06PE48

```c++
#include "allinclude.h"
bool findPath(BiTree root, TElemType target, SqStack2& path);

BiTree CommAncestor(BiTree root, TElemType c1, TElemType c2)
{  // Add your code here
   if(!root || root->data == c1 || root->data == c2)
   {
      return NULL;
   }

   BiTree parent = NULL;
   SElemType temp;
   temp.ptr = NULL;
   SqStack2 S1,S2,Sq,Sp;
   InitStack_Sq2(S1);
   InitStack_Sq2(S2);
   InitStack_Sq2(Sq);
   InitStack_Sq2(Sp);

   if(!findPath(root,c1,Sp) || !findPath(root,c2,Sq))
      return NULL;

   while (!StackEmpty_Sq2(Sp)) {
      Pop_Sq2(Sp,temp);
      Push_Sq2(S1,temp);
   }

   while (!StackEmpty_Sq2(Sq)) {
      Pop_Sq2(Sq,temp);
      Push_Sq2(S2,temp);
   }

   SElemType temp1,temp2;
   temp1.ptr = temp2.ptr = NULL;
   do{
      parent = temp1.ptr;

      GetTop_Sq2(S1,temp);
      if(temp.ptr->data == c1) break;
      GetTop_Sq2(S2,temp);
      if(temp.ptr->data == c2) break;

      Pop_Sq2(S1,temp1);
      Pop_Sq2(S2,temp2);
   }while(temp1.ptr == temp2.ptr);

   return parent;
}

bool findPath(BiTree root, TElemType target, SqStack2& path)
{
   if (!root) {
      return FALSE;
   }
   SElemType temp;
   temp.ptr = root;
   Push_Sq2(path,temp);
   if(root->data == target)
   {
      return TRUE;
   }
   
   if((root->lchild && findPath(root->lchild,target,path)) || (root->rchild && findPath(root->rchild,target,path)))
   {
      return true;
   }

   Pop_Sq2(path,temp);
   return FALSE;
}
```

### DC06PE49

```c++
#include "allinclude.h"
Status CompleteBiTree(BiTree bt)
{  // Add your code here
    if(!bt)
    {
        return TRUE;
    }

    bool hasNullBefore = FALSE;
    LQueue Q;
    InitQueue_LQ(Q);
    EnQueue_LQ(Q,bt);

    while(DeQueue_LQ(Q,bt))
    {
        if(bt->lchild)
        {
            if(!hasNullBefore)
            {
                EnQueue_LQ(Q,bt->lchild);
            }
            else {
                return FALSE;
            }
        }
        else {
            hasNullBefore = TRUE;
        }
        if(bt->rchild)
        {
            if(!hasNullBefore)
            {
                EnQueue_LQ(Q,bt->rchild);
            }
            else {
                return FALSE;
            }
        }  
        else {
            hasNullBefore = TRUE;
        }
    }
    return TRUE;
}
```

### DC06PE50

```c++
#include "allinclude.h"
Status  BTEqual(BiTree T1, BiTree T2)
{  // Add your code here
    if(!T1 && !T2)
    {
        return TRUE;
    }
    else if(!T1 || !T2){
        return FALSE;
    }

    if(T1->data == T2->data && BTEqual(T1->lchild,T2->lchild) && BTEqual(T1->rchild,T2->rchild))
    {
        return TRUE;
    }
    else {
        return FALSE;
    }
}
```

### DC06PE51

```c++
#include "allinclude.h"
void Degree1(BiTree T,int &count)
{  // Add your code here
    if(!T)
    {
        return ;
    }
    else if(!T->lchild && !T->rchild)
    {
        return ;
    }
    else if(!T->lchild || !T->rchild)
    {
        count++;
    }
    Degree1(T->lchild,count);
    Degree1(T->rchild,count);
}
```

### DC06PE52

```c++
#include "allinclude.h"
int BranchNodes(BiTree T)
{  // Add your code here
    if(!T)
    {
        return 0;
    }

    if(!T->lchild && !T->rchild)    //判断是否为叶子节点
    {
        return 0;
    }

    return 1 + BranchNodes(T->lchild) + BranchNodes(T->rchild);
}
```

### DC06PE53

```c++
#include "allinclude.h"
int LevelSum(BiTree T)
{  // Add your code here
    if(!T)
    {
        return 0;
    }

    int count = 0;
    LQueue Q;
    InitQueue_LQ(Q);
    EnQueue_LQ(Q,T);

    while (DeQueue_LQ(Q,T)) {
        count++;
        if(T->lchild)
        {
            EnQueue_LQ(Q,T->lchild);
        }
        if(T->rchild)
        {
            EnQueue_LQ(Q,T->rchild);
        }
    }
    return count;
}
```

### DC06PE54

```c++
#include "allinclude.h"
void ChangeTree(BiTree &T)
{  // Add your code here
    if(!T)
    {
        return ;
    }
    if(!T->lchild && T->rchild) //如果T没有左孩子但有右孩子
    {
        T->lchild = T->rchild;
        T->rchild = NULL;
    }

    ChangeTree(T->lchild);
    ChangeTree(T->rchild);
}
```

### DC06PE55

```c++
#include "allinclude.h"
#include <queue>
int Width(BiTree T)
{  // Add your code here
    if(!T) 
    {
        return 0;
    }
    
    queue<BiTNode*>q;
    q.push(T);
    int width = 0, res = 0;
    while(!q.empty()){
        width = q.size();
        if(width > res) res = width;
        for(int i=0; i<width; i++){
            BiTNode *node = q.front();
            q.pop();
            if(node->lchild) q.push(node->lchild);
            if(node->rchild) q.push(node->rchild);
        }
    }
    return res;
}
```

### DC06PE56

```c++
#include "allinclude.h"
Status SearchX(BiTree T, TElemType x)
{  // Add your code here
    if(!T)
    {
        return ERROR;
    }

    if(T->data == x)
    {
        return OK;
    }
    return SearchX(T->lchild,x) || SearchX(T->rchild,x);
}
```

### DC06PE57

```c++
#include "allinclude.h"
int NodeLevel(BiTree t, TElemType x)
{  // Add your code here
    if(!t)
    {
        return -1;
    }

    if(t->data == x)
    {
        return 1;
    }

    int level1,level2;
    level1=NodeLevel(t->lchild,x);
    level2=NodeLevel(t->rchild,x);
    
    if(level1!=-1 )
        return (level1+1);
    if(level2!=-1)  
        return (level2+1);
    
    return -1; 
}
```

### DC06PE58

```c++
#include "allinclude.h"
int countTree(BiTree T)
{
    if(!T)
    {
        return 0;
    }
    return 1+countTree(T->lchild)+countTree(T->rchild);
}
int xSum(BiTree T, TElemType x)
{  // Add your code here
    if(!T)
    {
        return 0;
    }

    if(T->data == x)
    {
        return countTree(T);
    }
    
    int count1,count2;
    count1 = xSum(T->lchild,x);
    count2 = xSum(T->rchild,x);

    return count1>count2?count1:count2; 
}
```

### DC06PE59

```c++
#include "allinclude.h"
void xLevel(BiTree T,TElemType x, bool &found, int &xlev)
{  // Add your code here
    if(!T)
    {
        found = FALSE;
        xlev = 0;
        return;
    }
    if(T->data == x)
    {
        found = TRUE;
        xlev++;
    }
    else {
        xlev++;
        int temp=xlev;                  //记录当前层次，用于后面回溯
        xLevel(T->lchild,x,found,xlev);
    
        if(!found)
        { 
            xlev=temp;
            xLevel(T->rchild,x,found,xlev); 
        }  
    }
}
```

### DC06PE60

```c++
#include "allinclude.h"
Status RegularBiTree(BiTree T)
{  // Add your code here
    if(!T)      //空树
    {
        return TRUE;
    }

    if(!(T->lchild && T->rchild || !T->lchild && !T->rchild))   //若度为1
    {
        return FALSE;
    }

    return RegularBiTree(T->lchild) && RegularBiTree(T->rchild);
}

```

### DC06PE61

```c++
#include "allinclude.h"
Status SmallBiTree(BiTree T)
{  // Add your code here
    if(!T)
    {
        return TRUE;
    }

    bool small1 = TRUE,small2 = TRUE;
    if (T->lchild) {
        if(T->data < T->lchild->data)
        {
            small1 = SmallBiTree(T->lchild);
        }
        else {
            small1 = FALSE;
        }
    }
    if (T->rchild) {
        if(T->data < T->rchild->data)
        {
            small2 = SmallBiTree(T->lchild);
        }
        else {
            small2 = FALSE;
        }
    }
    return small1 && small2;
}
```

### DC06PE62

```c++
#include "allinclude.h"
#include <queue>
int Width(BiTree T)
{  // Add your code here
    if(!T) 
    {
        return 0;
    }
    
    queue<BiTNode*>q;
    q.push(T);
    int width = 0, res = 0;
    while(!q.empty()){
        width = q.size();
        if(width > res) res = width;
        for(int i=0; i<width; i++){
            BiTNode *node = q.front();
            q.pop();
            if(node->lchild) q.push(node->lchild);
            if(node->rchild) q.push(node->rchild);
        }
    }
    return res;
}
```

### DC06PE65

```c++
#include "allinclude.h"  //DO NOT edit this line
/*
    way1
*/

// Status IsBSTree(BSTree T) 
// {   // Add your code here
//     if(!T)
//     {
//         return TRUE;
//     }

//     if(T->lchild)
//     {
//         if(T->data.key < T->lchild->data.key)
//         {
//             return FALSE;
//         }
//     }

//     if(T->rchild)
//     {
//         if(T->data.key > T->rchild->data.key)
//         {
//             return FALSE;
//         }
//     }

//     return IsBSTree(T->lchild) && IsBSTree(T->rchild);
// }

/*
    way2
*/

Status IsBSTree(BSTree T) 
{   // Add your code here
    if(!T)
    {
        return TRUE;
    }

    bool flag1,flag2;
    flag1 = flag2 = TRUE;

    if(T->lchild)
    {
        if(T->data.key > T->lchild->data.key)
        {
            flag1 = IsBSTree(T->lchild);
        }
        else {
            flag1 = FALSE;
        }
    }

    if(T->rchild)
    {
        if(T->data.key < T->rchild->data.key)
        {
            flag2 = IsBSTree(T->rchild);
        }
        else {
            flag2 = FALSE;
        }
    }

    return flag1 && flag2;
}
```

### DC06PE66

```c++
#include "allinclude.h"  //DO NOT edit this line
void OrderOut(BSTree T, KeyType k, void(*visit)(TElemType))
{   // Add your code here
    if(!T)
    {
        return ;
    }
    
    OrderOut(T->rchild,k,visit);

    if(T->data.key >= k)
    {
        visit(T->data);
    }

    OrderOut(T->lchild,k,visit);
}
```

### DC06PE67

```c++
#include "allinclude.h"  //DO NOT edit this line
Status InsertBST_I(BSTree &T, TElemType k) 
{    // Add your code here
    if(!T)
    {
        T = (BSTree)malloc(sizeof(BSTNode));
        T->lchild = T->rchild = NULL;
        T->data = k;
        return TRUE;
    }

    BSTree temp = T;
    while(temp)
    {
        //二叉搜索树，遵循左小右大原则，左子树节点值比根节点值小，右子树节点值比根节点值大
        if(temp->data.key < k.key)
        {
            if(temp->rchild)
            {
                temp = temp->rchild;
            }
            else {
                temp->rchild = (BSTree)malloc(sizeof(BSTNode));
                temp->rchild->data = k;
                temp->rchild->lchild = temp->rchild->rchild = NULL;
                return TRUE;
            }
        }
        else if(temp->data.key > k.key)
        {
            if(temp->lchild)
            {
                temp = temp->lchild;
            }
            else {
                temp->lchild = (BSTree)malloc(sizeof(BSTNode));
                temp->lchild->data = k;
                temp->lchild->lchild = temp->lchild->rchild = NULL;
                return TRUE;
            }
        }
        else {      //已经有等于k的值，插入不进去
            return FALSE;
        }
    }
    return FALSE;
}
```

### DC06PE68

```c++
#include "allinclude.h"  //DO NOT edit this line

bool findPath(BiTree T, TElemType target, Stack& path);

BiTree CommAncestor(BiTree T, TElemType a, TElemType b) 
{    // Add your code here
   if(!T || T->data == a || T->data == b)
   {
      return NULL;
   }

   BiTree parent = NULL;
   SElemType temp;
   temp.ptr = NULL;
   Stack S1,S2,Sq,Sp;
   InitStack(S1);
   InitStack(S2);
   InitStack(Sq);
   InitStack(Sp);

    if(!findPath(T,a,Sp) || !findPath(T,b,Sq))      //若任意一个元素在树中不存在
        return NULL;

    while (!StackEmpty(Sp)) {
        Pop(Sp,temp);
        Push(S1,temp);
    }

    while (!StackEmpty(Sq)) {
        Pop(Sq,temp);
        Push(S2,temp);
    }

   SElemType temp1,temp2;
   temp1.ptr = temp2.ptr = NULL;
   do{
      parent = temp1.ptr;

      GetTop(S1,temp);
      if(temp.ptr->data == a) break;
      GetTop(S2,temp);
      if(temp.ptr->data == b) break;

      Pop(S1,temp1);
      Pop(S2,temp2);
   }while(temp1.ptr == temp2.ptr);

   return parent;
}

bool findPath(BiTree T, TElemType target, Stack& path)
{
   if (!T) {
      return FALSE;
   }
   SElemType temp;
   temp.ptr = T;
   Push(path,temp);
   if(T->data == target)
   {
      return TRUE;
   }
   
   if((T->lchild && findPath(T->lchild,target,path)) || (T->rchild && findPath(T->rchild,target,path)))
   {
      return true;
   }

   Pop(path,temp);
   return FALSE;

}
```

### DC06PE69

```c++
#include "allinclude.h"  //DO NOT edit this line
void treeToString(BiTree T, string &str);
char* BiTree2String(BiTree T)
{   // Add your code here
    string str = "";
    treeToString(T, str);
    char *res = new char[str.size() + 1];
    strcpy(res, str.c_str());
    return res;
}

void treeToString(BiTree T, string &str) {
    if (!T) {
        str += "#";
        return ;
    }
    str += T->data; 
    if (T->lchild || T->rchild) {
        str += '(';
        treeToString(T->lchild, str);
        str += ',';
        treeToString(T->rchild, str);
        str += ')';
    }
}
```

### DC06PE75

```c++
#include "allinclude.h"  //DO NOT edit this line
BSTNode *Ranking(BSTree T, int k) 
{    // Add your code here
    if(!T)                  //空树或者没找到
        return NULL;
    if(T->lsize == k)       //找到了第k小结点
        return T;
    else if (T->lsize < k)  //往右找
        return Ranking(T->rchild,k-(T->lsize));
    else                    //往左找
        return Ranking(T->lchild,k);
}
```

## 第7章

### DC07PE15

```c++
#include "allinclude.h"  //DO NOT edit this line
int Leave(CSTree T) 
{   // Add your code here
    if(!T)
    {
        return 0;
    }

    if(!T->firstChild)  //该节点没有儿子,说明是叶子节点
    {
        return 1 + Leave(T->nextSibling);
    }
    return Leave(T->firstChild) + Leave(T->nextSibling);
}
```

### DC07PE17

```c++
#include "allinclude.h"  //DO NOT edit this line
int Degree(CSTree T) 
{   // Add your code here
    if(!T)
    {
        return 0;
    }

    int currentDegree = 0,childMaxDegree = 0;
    CSTree temp = NULL;
    if(T->firstChild)
    {
        currentDegree++;
        temp = T->firstChild->nextSibling;
    }
    while(temp)
    {
        currentDegree++;
        temp = temp->nextSibling;
    }
    childMaxDegree = Degree(T->firstChild) > Degree(T->nextSibling) ? Degree(T->firstChild):Degree(T->nextSibling);
    return currentDegree > childMaxDegree ?currentDegree:childMaxDegree;
}
```

### DC07PE22

```c++
#include "allinclude.h"  //DO NOT edit this line
int PTreeDepth(PTree T) 
{   // Add your code here
    if(!T.nodes)
        return 0;
    int depth = 1;  //若只有一个结点，则深度为1
    for(int i = T.nodeNum-1; i >= 0; --i)
    {
        int t = i,tempDepth = 1;
        while(t != T.r)
        {
            tempDepth++;
            t = T.nodes[t].parent;
        }
        depth = depth > tempDepth ? depth: tempDepth;
    }
    return depth;
}
```

### DC07PE24

```c++
#include "allinclude.h"  //DO NOT edit this line
int PCTreeDepth(PCTree T) 
{    // Add your code here
    if(T.n == 0) 
    {
        return 0;
    }
    int depth = 0, n = T.n;
    PCTreeNode node;
    while(n > 0){
        int count = 0;
        node = T.nodes[--n];
        while(node.parent != -1){
            count++;
            node = T.nodes[node.parent];
        }
        if(count > depth) depth = count;
    }
    return depth + 1;
}
```

### DC07PE26

```c++
#include "allinclude.h"  //DO NOT edit this line
int TreeDepth(CSTree T)
{   // Add your code here
    if(!T)
        return 0;
    return 1+TreeDepth(T->firstChild)>TreeDepth(T->nextSibling)?1+TreeDepth(T->firstChild):TreeDepth(T->nextSibling);
    // 一种比较简洁的写法
}
```

### DC07PE63

```c++
#include "allinclude.h"  //DO NOT edit this line
int find(MFSet S, int i) 
{   // Add your code here
    if (i < 0 || i >= S.n)
        return ERROR;
    int parent = i, temp = i;
    while (S.parent[parent] >= 0)       //若还没到根结点
        parent = S.parent[parent];
    while (S.parent[i] >= 0 && i >= 0)  //对路径上经过的结点进行路径压缩
    {
        temp = S.parent[i];
        S.parent[i] = parent;
        i = temp;
    }
    return parent;
}
```

## 第8章

### DC08PE12

```c++
#include "allinclude.h"  //DO NOT edit this line
Status CreateDG(MGraph &G, VexType *vexs, int n,
                           ArcInfo *arcs, int e) 
{    // Add your code here
    if(InitGraph(G,DG,n))
    {
        G.n = n;
        G.e = e;
        for (int i = 0; i < n; i++) {
            G.vexs[i] = vexs[i];
        }
        for(int i = 0; i < MAX_VEX_NUM; i++)
        {
            for(int j = 0; j < MAX_VEX_NUM; j++)
            {
                G.arcs[i][j].adj = 0;
            }
        }
        for(int i = 0; i < e; i++)
        {
            G.arcs[LocateVex(G,arcs[i].v)][LocateVex(G,arcs[i].w)].adj = 1;
        }
        return TRUE;
    }
    return FALSE;
}
```

### DC08PE15

```c++
#include "allinclude.h"  //DO NOT edit this line
int NextAdjVex(MGraph G, int k, int m) 
{   // Add your code here
    if(G.n == 0)
    {
        return -1;
    }

    if(k < 0 || k > G.n || G.e < 2) 
    {
        return -1;
    }
    for(int i=m+1; i<G.n; i++) {
        if(G.kind == UDG || G.kind == DG && G.arcs[k][i].adj == 1 && i != k) 
            return i;
        // if(G.arcs[k][i].adj != INFINITY && i != k) 
        //     return i;
    }
    return -1;
}
```

### DC08PE17

```c++
#include "allinclude.h"  //DO NOT edit this line
Status SetArc(MGraph &G, VexType v, VexType w, ArcCell info) 
{  // Add your code here
    int k = LocateVex(G,v);
    int m = LocateVex(G,w);
    if (k < 0 || k >= G.n || m < 0 || m >= G.n)
        return ERROR;   // k顶点或m顶点不存在
    if(G.kind == UDG || G.kind == UDN)
        G.arcs[k][m] = G.arcs[m][k] = info;
    else
        G.arcs[k][m] = info;
    return OK;
}
```

### DC08PE21

```c++
#include "allinclude.h"  //DO NOT edit this line
int outDegree(ALGraph G, int k) 
{  // Add your code here
    if(k < 0 || k >= G.n)
        return -1;
    int out_degree = 0;
    AdjVexNodeP p = G.vexs[k].firstArc;
    while (p) {
        p = p->next;
        out_degree++;
    }
    return out_degree;
}
```

### DC08PE32

```c++
#include "allinclude.h"  //DO NOT edit this line
Status CreateDG(ALGraph &G, VexType *vexs, int n,
                            ArcInfo *arcs, int e) 
{  // Add your code here
    int i, j, k;
    VexType v, w;
    AdjVexNodeP p;
    G.n = n;
    G.e = e;
    G.tags = (int *)malloc(sizeof(int) * n);
    for (i = 0; i < n; ++i)
    {
        G.vexs[i].data = vexs[i];
        G.vexs[i].firstArc = NULL;
        G.tags[i] = UNVISITED;
    }
    for (k = 0; k < G.e; ++k)
    {
        v = arcs[k].v;
        w = arcs[k].w;
        i = LocateVex(G, v);
        j = LocateVex(G, w);
        if (i < 0 || j < 0) // v或w顶点不存在
            return ERROR;
        // 有向边创建,只需要创建一条
        p = (AdjVexNodeP)malloc(sizeof(AdjVexNode));
        if (p == NULL)
            return ERROR;
        p->info = 1;
        p->adjvex = j;
        p->next = G.vexs[i].firstArc;
        G.vexs[i].firstArc = p;
    }
    return OK;
}
```

### DC08PE34

```c++
#include "allinclude.h"  //DO NOT edit this line
Status CreateUDG(ALGraph &G, VexType *vexs, int n,
                             ArcInfo *arcs, int e) 
{  // Add your code here
    int i, j, k;
    VexType v, w;
    AdjVexNodeP p;
    G.n = n;
    G.e = e;
    G.tags = (int *)malloc(sizeof(int) * n);
    for (i = 0; i < n; ++i)
    {
        G.vexs[i].data = vexs[i];
        G.vexs[i].firstArc = NULL;
        G.tags[i] = UNVISITED;
    }
    for (k = 0; k < G.e; ++k)
    {
        v = arcs[k].v;
        w = arcs[k].w;
        if (v == w) // 无向图无自环
            continue;
        i = LocateVex(G, v);
        j = LocateVex(G, w);
        if (i < 0 || j < 0) // v或w顶点不存在
            return ERROR;
        // 无向边创建,需要创建两条
        p = (AdjVexNodeP)malloc(sizeof(AdjVexNode));
        if (p == NULL)
            return ERROR;
        p->info = 1;
        p->adjvex = j;
        p->next = G.vexs[i].firstArc;
        G.vexs[i].firstArc = p;

        p = (AdjVexNodeP)malloc(sizeof(AdjVexNode));
        if (p == NULL)
            return ERROR;
        p->info = 1;
        p->adjvex = i;
        p->next = G.vexs[j].firstArc;
        G.vexs[j].firstArc = p;
    }
    return OK;
}
```

## 说明

代码基本都是我手敲的，若有纰漏，还请见谅。

也欢迎大家及时指正，更新题库。

[By WiseL00k](https://github.com/WiseL00k)
