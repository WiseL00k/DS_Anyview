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



## 未完待续...

[By WiseL00k](https://github.com/WiseL00k)

