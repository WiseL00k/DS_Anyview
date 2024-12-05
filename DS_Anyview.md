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

## 未完待续...

[By WiseL00k](https://github.com/WiseL00k)

