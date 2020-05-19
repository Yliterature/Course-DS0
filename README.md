|作者|literature|
|---|---
|时间|2020.05.20

:satisfied: 本仓库由[litreature](https://literature.k6366.com.cn/)维护<br>
邮箱:2440229611@qq.com  or  22012245@sfcollege.edu

# 食用须知
本仓库代码开源，仅供学习交流！利用本仓库代码进行学术造假和商业获利造成的后果，均与本仓库维护人员无关！


## 实验平台<br>
[NJUPT Online Judge](https://acm.njupt.edu.cn)<br>

## 实验一<br>
[NOJ1004 线性表操作](https://acm.njupt.edu.cn/problem/NOJ1004)<br>
```C
/*************************************************
Copyright (C), 2018-2022,Literature Tech. Co., Ltd.
source:    南京邮电大学《数据结构A》课程实验 NOJ1004
Author:    Written by Mr.YangWenxuan
Version:   1.0
Date:      2020.05.20
Description:  线性表是n个元素的有序集合（n≥0），n是线性表中元素的个数，
              称为线性表的长度。可以用一组地址连续的存储单元依次存储线性表中元素，
              采用这种存储方式的线性表称为顺序表。
              请在顺序表上实现运算，实现顺序表的逆置，删除表中所有元素值等于x的元素。
Others:   None
Function List:  main
History:  The first edition 2020.05.19
*************************************************/

#include<stdio.h>
#include<stdlib.h>
int main()
{
    int k, *a, A;
	int n1, n2, n3;
	char *c, B;
	double *d, C;
	//输入 
	/*************************/ 
	scanf("%d", &n1);
	//动态申请数组空间存入元素 
	a = (int*)malloc(sizeof(int)*n1);
	for (k = 0;k < n1;k++)		
		{
		    scanf("%d", &a[k]);
		}
	scanf("%d", &A);	
	scanf("%d\n", &n2);	
	//动态申请数组空间存入元素 
	c = (char*)malloc(sizeof(char)*n2);	
	for (k = 0;k < n2;k++)	
		{
		    scanf("%c ", c+k);	
		}
	scanf("%c", &B);	
	scanf("%d", &n3);
	//动态申请数组空间存入元素 
	d = (double*)malloc(sizeof(double)*n3);	
	for (k = 0;k < n3;k++)		
	    {
		    scanf("%lf", &d[k]);
		}
	scanf("%lf", &C);
	//输出
	/************************/				
	for (k = n1 - 1;k >= 0;k--)	 //逆序输出 
		{
		    printf("%d ", a[k]);
		}
	printf("\n");
	for (k = n1 - 1;k >= 0;k--)	
		{
			if (a[k] == A)        //排除相同元素 
				continue;	
			printf("%d ", a[k]);	
		}
	printf("\n");
	for (k = n2 - 1;k >= 0;k--)	 //逆序输出 
		{
		    printf("%c ", c[k]);
		}
    printf("\n");	
	for (k = n2 - 1;k >= 0;k--)	  //排除相同元素
		{
		    if (c[k] == B)		
				continue;	
			printf("%c ", c[k]);
		}
	printf("\n");
	for (k = n3 - 1;k >= 0;k--)	   //逆序输出 
	    {
		    printf("%g ", d[k]);   
		}
	printf("\n");
	for (k = n3 - 1;k >= 0;k--)   //排除相同元素
		{		
			if (d[k] == C)		
				continue;	
			printf("%g ", d[k]);
		}
    return 0;

}
```

[NOJ1005 多项式加法](https://acm.njupt.edu.cn/problem/NOJ1005)<br>
```C++
/*************************************************
Copyright (C++), 2018-2022,Literature Tech. Co., Ltd.
source:    南京邮电大学《数据结构A》课程实验 NOJ1005
Author:    Written by Mr.YangWenxuan
Version:   1.0
Date:      2020.05.20
Description:  线性表是一种最简单、最基本，也是最常用的数据结构，其用途十分广泛，
              例如，用带表头结点的单链表求解一元整系数多项式加法和乘法运算。
	      现给两个一元整系数多项式，请求解两者之和。
Others:   None
Function List:  main
History:  The first edition 2020.05.19
*************************************************/
#include<iostream>
#include<stdio.h>
#include<malloc.h>
using namespace std;
   struct node
   {
       int x,z;
       node *next;
       node(int a,int b):x(a),z(b),next(NULL){}
   };
void print(node *head)
{
       node *q=head->next;
       if(q==NULL)
         printf("0");
       else
       {
           int f=1,f2=0;
           while(q)
           {
               if(q==head->next)
               {
                   if(q->x!=1)
                   {
                       if(q->x==-1)
                            printf("-");
                       else
                           printf("%d",q->x);
                   }
               }
               else
               {
                   if(q->x>0)
                   {
                       printf("+");
                       if(q->x!=1)
                            printf("%d",q->x);
                   }
                    else
                    {
                        if(q->x!=-1)
                            printf("%d",q->x);
                        else
                            printf("-");
                    }
               }
               if(q->z!=0)
                    printf("X");
               else
               {
                   if(q->x==1||q->x==-1)
                        printf("1");
                   q=q->next;
                   continue;
               }
               if(q->z!=1)
                    printf("^%d",q->z);
               q=q->next;
           }
       }
        printf("\n");
}
   int main()
   {
       node *tail,*tail1,*tmp,*hea,*hea1;
       int n,m,f=1;
       tail=new node(0,0);
       while(scanf("%d%d",&n,&m)&&(n!=0||m!=-1))
       {
           if(n==0)
                continue;
           tmp=new node(n,m);
           if(tail->z==tmp->z)
             tail->x=tail->x+tmp->x;
           else
           {
             tail->next=tmp;
             tail=tmp;
           }
           if(f)
           {
               hea=new node(0,0);
               tmp->next=hea->next;
               hea->next=tmp;
           }
           f=0;
       }
       print(hea);
       f=1;
       tail1=new node(0,0);
       while(scanf("%d%d",&n,&m)&&(n!=0||m!=-1))
       {
           if(n==0)
                continue;
           node *p=hea,*q=hea->next,*cur,*tmp1;
           int f1=0;
           cur=new node(n,m);
           tmp1=new node(n,m);
           if(tail1->z==tmp1->z)
             tail1->x=tail1->x+tmp1->x;
           else
           {
               tail1->next=tmp1;
               tail1=tmp1;
           }
           if(f)
           {
               hea1=new node(0,0);
               tmp1->next=hea1->next;
               hea1->next=tmp1;
           }
           while(q)
           {
               if(q->z==cur->z)
               {
                   f1=1;
                   q->x=cur->x+q->x;
                   if(q->x==0)
                   {
                       p->next=q->next;
                       delete q;
                       q=p->next;
                   }
                   break;
               }
               if(q->z<cur->z)
               {
                   f1=1;
                   p->next=cur;
                   cur->next=q;
                   break;
               }
               p=p->next;
               q=p->next;
           }
           if(!f1)
           {
               p->next=cur;
               cur->next=NULL;
           }
           f=0;
       }
       print(hea1);
       print(hea);
       return 0;
}
```

[NOJ1006 多项式乘法](https://acm.njupt.edu.cn/problem/NOJ1006)<br>
```C++
/*************************************************
Copyright (C), 2018-2022,Literature Tech. Co., Ltd.
source:    南京邮电大学《数据结构A》课程实验 NOJ1006
Author:    Written by Mr.YangWenxuan
Version:   1.0
Date:      2020.05.20
Description:  线性表是一种最简单、最基本，也是最常用的数据结构，其用途十分广泛，
              例如，用带表头结点的单链表求解一元整系数多项式加法和乘法运算。    
              现给两个一元整系数多项式，请求解两者的乘积。
Others:   None
Function List:  main
History:  The first edition 2020.05.19
*************************************************/
#include <iostream>
#include <cstdio>
#include <cstring>
#include <algorithm>
using namespace std;
const int maxn=10000+5;
int ax[maxn],ay[maxn];
int bx[maxn],by[maxn];
int cy[maxn],c[maxn];
int main(void)
{
    int x,y;
    bool q=false;
    memset(ax,0,sizeof(ax));
    memset(bx,0,sizeof(bx));
    memset(ay,0,sizeof(ay));
    memset(by,0,sizeof(by));
    bool f=true;
    int n=0,m=0;
    while(scanf("%d%d",&x,&y))
    {
        if(x==0 && y==-1)
            break;
        ax[n]=x;
        ay[n++]=y;
    }
    while(scanf("%d%d",&x,&y))
    {
        if(x==0 && y==-1)
            break;
        bx[m]=x;
        by[m++]=y;
    }
    for(int i=0;i<n;i++)
    {
        if(ax[i]==0)
            continue;
        if(ax[i]!=1 && (f || ax[i]<0))
        {
            if(ax[i]==-1 && ay[i]!=0)
                printf("-");
            else
                printf("%d",ax[i]);
        }
        else
        { 
            if(ax[i]==1)
            {
                if(f)
                {
                    if(ay[i]==0)
                        printf("1");
                }
                else
                {
                    if(ay[i]==0)
                        printf("+1");
                    else
                        printf("+");
                }
            }
            else if(ax[i]!=1 && !f)
                printf("+%d", ax[i]);
        }
        if(ay[i]==1)
            printf("X");
        else if(ay[i]!=0)
            printf("X^%d", ay[i]);
        f=false;
    }
    printf("\n");
    f=true;
    for(int i=0;i<m;i++)
    {
        if(bx[i]==0)
            continue;
        if(bx[i]!=1 && (f || bx[i]<0))
        {
            if(bx[i]==-1 && by[i]!=0)
                printf("-");
            else
                printf("%d",bx[i]);
        }
        else
        {
            if(bx[i]==1)
            {
                if(f)
                {
                    if(by[i]==0)
                        printf("1");
                }
                else
                {
                    if(by[i]==0)
                        printf("+1");
                    else
                        printf("+");
                }
            }
            else if(bx[i]!=1 && !f)
                printf("+%d", bx[i]);
        }
        if(by[i]==1)
            printf("X");
        else if(by[i]!=0)
            printf("X^%d", by[i]);
        f=false;
    }
    printf("\n");
    f=true;
    int len=0;
    memset(c,0,sizeof(c));
    for(int i=0;i<n;i++)
        for(int j=0;j<m;j++)
        {
            x=ax[i]*bx[j];
            y=ay[i]+by[j];
            cy[len++]=y;
            c[y]+=x;
        //  printf("%d %d\n",x,y );
        }
    sort(cy,cy+len);
    len=unique(cy,cy+len)-cy;
    for(int i=len-1;i>=0;i--)
    {
        if(c[cy[i]]==0)
            continue;
        if(c[cy[i]]!=1 && (f || c[cy[i]]<0))
        {
            if(c[cy[i]]==-1 && cy[i]!=0)
                printf("-");
            else
                printf("%d",c[cy[i]]);
        }
        else
        { 
            if(c[cy[i]]==1)
            {
                if(f)
                {
                    if(cy[i]==0)
                        printf("1");
                }
                else
                {
                    if(cy[i]==0)
                        printf("+1");
                    else
                        printf("+");
                }
            }
            else if(c[cy[i]]!=1 && !f)
                printf("+%d", c[cy[i]]);
        }
        if(cy[i]==1)
            printf("X");
        else if(cy[i]!=0)
            printf("X^%d", cy[i]);
        f=false;
        q=true;
    }
    if(q)
        printf("\n");
    else
        printf("0\n");
}
```

## 实验二<br>
[NOJ1018 深度遍历二叉树](https://acm.njupt.edu.cn/problem/NOJ1018)<br>
```C
/*************************************************
Copyright (C), 2018-2022,Literature Tech. Co., Ltd.
source:    南京邮电大学《数据结构A》课程实验 NOJ1018
Author:    Written by Mr.YangWenxuan
Version:   1.0
Date:      2020.05.20
Description:  二叉树(binary tree)是非常重要的树形数据结构，它是结点的有限集合，该集合或者为空集，
              或者是由一个根和两个互不相交的、称为该根的左子树和右子树的二叉树组成。
Others:   None
Function List:  main
History:  The first edition 2020.05.19
*************************************************/

#include <stdio.h>
#include <stdlib.h>

/* @define ElemType */
typedef char ElemType;

char *c = "DEH##FJ##G#CK###A#B##";

/* @struct BinaryTreeNode */
typedef struct BinaryTreeNode
{
	ElemType Data;
	struct BinaryTreeNode *lChild, *rChild;
}BinaryTreeNode;
typedef BinaryTreeNode* BiTree;

/* @struct BinaryTree */
typedef struct BinaryTree
{
	BinaryTreeNode *root;
}BinaryTree;


void PreOrderTransverse(BiTree t)
{
	if (t == NULL)
		return;
	printf(" %c", t->Data);
	PreOrderTransverse(t->lChild);
	PreOrderTransverse(t->rChild);
}

void InOrderTransverse(BiTree t)
{
	if (t == NULL)
		return;
	InOrderTransverse(t->lChild);
	printf(" %c", t->Data);
	InOrderTransverse(t->rChild);
}

void PostOrderTransverse(BiTree t)
{
	if (t == NULL)
		return;
	PostOrderTransverse(t->lChild);
	PostOrderTransverse(t->rChild);
	printf(" %c", t->Data);
}

BinaryTreeNode* PreCreateBt(BinaryTreeNode *t)
{
	char ch;
	ch = *c++;
	if (ch == '#')
		t = NULL;
	else
	{
		t = (BinaryTreeNode*)malloc(sizeof(BinaryTreeNode));
		t->Data = ch;
		t->lChild = PreCreateBt(t->lChild);
		t->rChild = PreCreateBt(t->rChild);
	}
	return t;
}

int main()
{
	BinaryTree myTree;
	myTree.root = NULL;
	myTree.root = PreCreateBt(myTree.root);
	printf("PreOrder:");
	PreOrderTransverse(myTree.root);
	printf("\n");
	printf("InOrder:");
	InOrderTransverse(myTree.root);
	printf("\n");
	printf("PostOrder:");
	PostOrderTransverse(myTree.root);
	printf("\n");
	return 0;
}
```

[NOJ1019 计算二叉树的高度和结点数](https://acm.njupt.edu.cn/problem/NOJ1019)<br>
```C++
/*************************************************
Copyright (C), 2018-2022,Literature Tech. Co., Ltd.
source:    南京邮电大学《数据结构A》课程实验 NOJ1019
Author:    Written by Mr.YangWenxuan
Version:   1.0
Date:      2020.05.20
Description:  二叉树(binary tree)是非常重要的树形数据结构，它是结点的有限集合，该集合或者为空集，
              或者是由一个根和两个互不相交的、称为该根的左子树和右子树的二叉树组成。
Others:   None
Function List:  main
History:  The first edition 2020.05.19
*************************************************/

#include<iostream> 
using namespace std;
/* @struct BinaryTreeNode */
struct BinaryTreeNode 
{
	char n;
	struct BinaryTreeNode  *l;
	struct BinaryTreeNode  *r;
};
void PreCreatBt(BinaryTreeNode * &t)
{
	char ch;
	cin>>ch;
	if(ch == '#')
	{
		t=NULL;
	}
	else
	{
		t=(BinaryTreeNode*)malloc(sizeof(BinaryTreeNode));
		t->n=ch;
		PreCreatBt(t->l);
		PreCreatBt(t->r);
	}
}
void PreOrder(struct BinaryTreeNode  *t)
{
	if(t)
	{
		cout<<' '<<t->n;
		PreOrder(t->l);
		PreOrder(t->r);
	}
}
void InOrder(struct BinaryTreeNode  *t)
{
	if(t)
	{
		InOrder(t->l);
		cout<<' '<<t->n;
		InOrder(t->r);
	}
}
void PostOrder(struct BinaryTreeNode  *t)
{
	if(t)
	{
		PostOrder(t->l);
		PostOrder(t->r);
		cout<<' '<<t->n;
	}
}
int GetHigh(struct BinaryTreeNode  *t)
{
	if(t==NULL)
		return 0;
	int lhigh=GetHigh(t->l);
	int rhigh=GetHigh(t->r);
	if(lhigh>=rhigh)
		return lhigh+1;
	else
		return rhigh+1;
}
void GetAll(struct BinaryTreeNode  *t,int &flag)
{
	if(t)
	{
		if(!t->l&&!t->r)
			flag++;
		GetAll(t->l,flag);
		GetAll(t->r,flag);
	}
}
void GetLeaf(struct BinaryTreeNode  *t,int &flag1)
{
	if(t)
	{
		flag1++;
		GetLeaf(t->l,flag1);
		GetLeaf(t->r,flag1);
	}
}
void Get1(struct BinaryTreeNode  *t,int &flag2)
{
	if(t)
	{
		if((!(t->r))&&t->l)
		{
			flag2++;
			Get1(t->l,flag2);
		}
		if((!(t->l))&&t->r)
		{
			flag2++;
			Get1(t->r,flag2);
		}
		if(t->r&&t->l)
		{
			Get1(t->l,flag2);
			Get1(t->r,flag2);
		}
	}
}
int main()
{
	int flag=0;
	int flag1=0;
	int flag2=0;
	struct BinaryTreeNode  *t;
	PreCreatBt(t);
	cout<<"PreOrder:";
	PreOrder(t);
	cout<<endl;
	cout<<"InOrder:";
	InOrder(t);
	cout<<endl;
	cout<<"PostOrder:";
	PostOrder(t);
	cout<<endl;
	cout<<GetHigh(t)<<endl;
	GetLeaf(t,flag1);
	cout<<flag1<<' ';
	GetAll(t,flag);
	cout<<flag<<' ';
	Get1(t,flag2);
	cout<<flag2<<endl;
	return 0;
}
```

[NOJ1020 层次遍历二叉树](https://acm.njupt.edu.cn/problem/NOJ1020)<br>
```C++
/*************************************************
Copyright (C++), 2018-2022,Literature Tech. Co., Ltd.
source:    南京邮电大学《数据结构A》课程实验 NOJ1020
Author:    Written by Mr.YangWenxuan
Version:   1.0
Date:      2020.05.20
Description:  二叉树是非常重要的树形数据结构，层次遍历一棵二叉树是按从上到下、从左到右的次序访问树上的结点。
              例如，二叉树层次遍历序列为A B C D E F
Others:   None
Function List:  main
History:  The first edition 2020.05.19
*************************************************/
#include <cstdio>
#include <string>

int main() {
    std::string layer[30];
    int state[30] = {};
    int depth = 0;
    char c;

    while (scanf(" %c", &c) != EOF) {
        if (c == '#') {
            while (state[depth] == 2) --depth;
            ++state[depth];
            while (state[depth] == 2) --depth;
        } else {
            layer[depth] += c;
            ++state[depth];
            state[++depth] = 0;
        }
    }
    printf("LevelOrder:");
    for (const std::string &i : layer) {
        if (i.empty()) break;
        for (const char &j : i)
            printf(" %c", j);
    }
    putchar('\n');
    return 0;
}
```
### 内存泄露版（有人能改请提交邮箱22012245@sfcollege.edu or 2440229611@qq.com)
```C
#include<stdio.h>
#include<malloc.h>
#define MAXSIZE 10
typedef char dataType;

/***************结构体的定义***********/ 

//二叉树结构
typedef struct bnode
{
	dataType data;
	struct bnode *lChild,*rChild;
}Bnode,*BTree;

//队列结构
typedef struct 
{
	BTree data[MAXSIZE];
	int front,rear;
}SeqQueue,*PSeqQueue;

//栈的结构
typedef struct 
{
	BTree data[MAXSIZE];
	int top;
}SeqStack,*PSeqStack;
 
/******************队列的操作***********/ 

//队列的初始化
PSeqQueue initSeqQueue()
{
	PSeqQueue  queue;
	queue = (PSeqQueue)malloc(sizeof(SeqQueue));
	if(queue)
	{
		queue->front = queue->rear = 0;
	}
	return queue;
}

//判断队列是否为空
int emptyQueue(PSeqQueue queue)
{
	if(queue && queue->front==queue->rear)
	{
		return 1;
	}else
	{
		return 0;
	}
}

//入队列
int pushQueue(PSeqQueue queue,Bnode *node)
{
	if((queue->rear+1)%MAXSIZE == queue->front) //判断队列是否满了
	{
		return -1;
	}else
	{
		queue->rear = (queue->rear+1)%MAXSIZE;//位置为0的地址空间不用，方便判断是否为空
		queue->data[queue->rear] = node;
		return 1;
	}
}
//出队列

int popQueue(PSeqQueue queue,BTree *node)
{
	if(emptyQueue(queue))
	{
		return -1;
	}else
	{
		queue->front = (queue->front +1)%MAXSIZE;
		*node = queue->data[queue->front];
		return 1;
	}
}

//读取队头元素
int frontQueue(PSeqQueue queue,BTree *node)
{
	if(queue->rear == queue->front)
	{
		return -1;
	}else
	{
		*node = queue->data[(queue->front+1)%MAXSIZE];
		return 1;
	}
}

//销毁队列
void destroyQueue(PSeqQueue *queue)
{
	if(*queue)
	{
		free(*queue);
		*queue = NULL;
	}
}
/******************栈的基本操作*************/
 
//栈的初始化
PSeqStack initStack()
{
	PSeqStack stack;
	stack = (PSeqStack)malloc(sizeof(SeqStack));
	if(stack)
	{
		stack->top = -1;
	}
	return stack;
}

//判断栈是否为空    1,空;0,非空
int emptyStack(PSeqStack stack)
{
	if(stack->top == -1)
	{
		return 1;
	}else
	{
		return 0;
	}
}

//入栈
int pushStack(PSeqStack stack,Bnode *node)
{
	if(stack->top == MAXSIZE-1)
	{
		return 0;
	}else
	{
		stack->top ++;
		stack->data[stack->top] = node;
		return 1;
	}
}

//出栈
int popStack(PSeqStack stack,BTree *node)
{
	if(emptyStack(stack) == 1)
	{
		return 0;
	}else
	{
		*node = stack->data[stack->top];
		stack->top --;
		return 1;
	}
}

//打印元素
void visit(char ch)
{
	printf(" %c",ch);
}
 
/***************二叉树的建立************/ 
BTree createTree()
{
	BTree tree;
	dataType str;
	str = getchar();
	if(str == '#')
	{
		tree = NULL;
	}else
	{
		tree = (BTree)malloc(sizeof(Bnode));
		tree->data = str;
		tree->lChild = createTree();
		tree->rChild = createTree();
	}
	return tree;
}
/************二叉树的遍历算法************/ 

//层次遍历二叉树
void levelOrder(BTree tree )
{
	BTree p = tree;
	PSeqQueue queue = initSeqQueue();
	if(p)
	{
		pushQueue(queue,p);
		while(!emptyQueue(queue))
		{
			popQueue(queue,&p);
			visit(p->data);
			if(p->lChild)
			{
				pushQueue(queue,p->lChild);
			}
			if(p->rChild)
			{
				pushQueue(queue,p->rChild);
			}
		}
	}
}
/****************主函数*****************/ 
int main()
{
	BTree tree = createTree();
	int i=0;
	printf("LevelOrder:");
	levelOrder(tree );
	printf("\n");
	return 0;
}
```

[NOJ1021 二叉树复制和左右子树互换](https://acm.njupt.edu.cn/problem/NOJ1021)<br>
```C
//想不到吧，我也不会，给个解题思路吧
//其实整个题目没有什么难度，算是一道彻底的水题。左右子树的互换涉及到分治法的思想，即如果从根节点开始看，换根节点的左右子树。每个子树的根节点又互换它们的左右子树。那么子问题的解构成了原问题的解。而且与动态规划不同的是，子问题的解是相互独立的，故可以很方便的用递归求解出来。
发现分治和搜索都是递归的（当然也可以写成非递归，但是有点麻烦，本人较懒），而动态规划则会用一个备忘录记录子问题的解，需要时就会使用。故分治和搜索的时间复杂度就会比较高，通常是指数级别（尤其是问题域比较大时，搜索的时间复杂度会非常高，这就需要强剪枝），而动态规划思考非常难，但是一旦写出，时间复杂度会控制在n的平方或n的立方左右。 
```

[NOJ1022 哈夫曼编码与译码](https://acm.njupt.edu.cn/problem/NOJ1022)<br>
```C++
/*************************************************
Copyright (C), 2018-2022,Literature Tech. Co., Ltd.
source:    南京邮电大学《数据结构A》课程实验 NOJ1022
Author:    Written by Mr.YangWenxuan
Version:   1.0
Date:      2020.05.20
Description:  已知电文包括的字符集为{A，C，I，M，N，P，T，U}，
              输入对应权值，对字符集合进行哈夫曼编码，
              完成电文的哈夫曼编码与译码工作。
Others:   None
Function List:  main
History:  The first edition 2020.05.19
*************************************************/

#include<iostream>
#include<queue>
#include<string>
using namespace std;

/* @define MAX */
#define MAX 10
/* @variable temp */
char str[8]={'A','C','I','M','N','P','T','U'};
int temp[MAX*3];
int str2[256][MAX*3];
string str3;

//类定义
class node
{
    public:
    int k;
    char c;
    node *l,*r;
    node()
    {
        c='0';
        k=0;r=l=NULL;
    }
    node(int a,char s)
    {
        k=a;r=l=NULL;
        c=s;
    }
    friend node* uni(node *p,node *q)
    {
        node *temp=new node(p->k+q->k,'0');
        temp->l=p;
        temp->r=q;
        return temp;
    }
};
void prim(node *p,int L)
{
    if(!p->r)
    {
        str2[p->c][0]=L;
        for(int i=1;i<=L;i++)
        {
            str2[p->c][i]=temp[i-1];
        }
    }
    else
    {
        temp[L]=0;
        prim(p->l,L+1);
        temp[L]=1;
        prim(p->r,L+1);
    }
}
 
class nodeCmp
{
public:
    bool operator()(node* p1, node* p2) const
    {
        return p1->k > p2->k;
    }
};
node *s[MAX*3];
priority_queue<node *,deque<node *>,nodeCmp> pro_queue;
int main()
{
    //freopen("a.txt","r",stdin);
    int i,a;
    for(i=0;i<8;i++)
    {
        cin>>a;
        node *p;
        p=new node(a,str[i]);
        s[i]=p;
        pro_queue.push(s[i]);
    }
    while(pro_queue.size()>1)
    {
        node *p,*q,*k;
        p=pro_queue.top();
        pro_queue.pop();
        q=pro_queue.top();
        pro_queue.pop();
        k=uni(p,q);
        pro_queue.push(k);
        }
        node *p=pro_queue.top();
        prim(p,0);
        for(i=0;i<8;i++)
        {
            cout<<str[i]<<": ";
            for(int j=1;j<=str2[str[i]][0];j++)
            {
                cout<<str2[str[i]][j];
                }
                cout<<endl;
            }
            cin>>str3;
            int len=str3.length();
            for(i=0;i<len;i++)
            {
                for(int j=1;j<=str2[str3[i]][0];j++)
                {
                cout<<str2[str3[i]][j];
                }
            }
            cout<<endl;
            cin>>str3;
            len=str3.length();
            node *q=pro_queue.top();
            for(i=0;i<len;i++)
            {
 
                if(str3[i]=='1')
                {
                q=q->r;
                }
                else
                {
                q=q->l;
                }
                if(q->c!='0')
                {
                cout<<q->c;
                q=pro_queue.top();
                }
            }
            cout<<endl;
    return 0;
    }
```



## 实验三<br>
[NOJ1047 图的深度优先遍历序列](https://acm.njupt.edu.cn/problem/NOJ1047)<br>
```C
/*************************************************
Copyright (C), 2018-2022,Literature Tech. Co., Ltd.
source:    南京邮电大学《数据结构A》课程实验 NOJ1047
Author:    Written by Mr.YangWenxuan
Version:   1.0
Date:      2020.05.20
Description:  图(graph)是数据结构 G=(V,E)，其中V是G中结点的有限非空集合,结点的偶对称为边(edge)；
              E是G中边的有限集合。设V={0,1,2,……,n-1}，图中的结点又称为顶点(vertex)，
              有向图(directed graph)指图中代表边的偶对是有序的，
              用<u，v>代表一条有向边（又称为弧），则u称为该边的始点（尾），v称为边的终点（头）。
              无向图(undirected graph)指图中代表边的偶对是无序的，在无向图中边(u，v )和(v，u)是同一条边。
Others:   None
Function List:  main
History:  The first edition 2020.05.19
*************************************************/

#include<stdio.h>
#include<stdlib.h>

/* @define ElemType */
typedef int ElemType;

/* @struct mGraph */
typedef struct
{
	ElemType **a;
	int n;
	int e;
	ElemType noEdge;
}mGraph;

int Init(mGraph *mg, int nSize, int eNum)
{
	int i, j;
	mg->n = nSize;
	mg->e = eNum;
	mg->noEdge = 0;
	mg->a = (ElemType**)malloc(nSize * sizeof(ElemType*));
	if (!mg->a)
		return 0;
	for (i = 0;i < mg->n;i++)
	{
		mg->a[i] = (ElemType*)malloc(nSize * sizeof(ElemType));
		for (j = 0;j < mg->n;j++)
			mg->a[i][j] = mg->noEdge;
	}
	return 1;
}

int Insert(mGraph *mg, int u, int v)
{
	mg->a[u][v] = 1;
	return 1;
}

void Print(mGraph *mg)
{
	int i, j;
	for (i = 0;i < mg->n;i++)
	{
		for (j = 0;j < mg->n;j++)
			printf("%d ", mg->a[i][j]);
		printf("\n");
	}
}

void Destroy(mGraph *mg)
{
	int i;
	for (i = 0;i < mg->n;i++)
		free(mg->a[i]);
	free(mg->a);
}

void DFS(int u, mGraph mg, int visited[])
{
	int i;
	printf("%d ", u);
	visited[u] = 1;
	for (i = 0;i < mg.n;i++)
		if (mg.a[u][i] != 0 && !visited[i])
			DFS(i, mg, visited);
}

void DFSgraph(mGraph mg)
{
	int i, *visited;
	visited = (int*)malloc(sizeof(int)*mg.n);
	for (i = 0;i < mg.n;i++)
		visited[i] = 0;
	for (i = 0;i < mg.n;i++)
		if (!visited[i])
			DFS(i, mg, visited);
}

int main()
{
	mGraph graph;
	int n, e, u, v, i;
	scanf("%d%d", &n, &e);
	Init(&graph, n, e);
	for (i = 0;i < e;i++)
	{
		scanf("%d%d", &u, &v);
		Insert(&graph, u, v);
		Insert(&graph, v, u);
	}
	Print(&graph);
	DFSgraph(graph);
	Destroy(&graph);
	return 0;
}
```

[NOJ1048 图的宽度优先遍历序列](https://acm.njupt.edu.cn/problem/NOJ1048)<br>
```C
/*************************************************
Copyright (C), 2018-2022,Literature Tech. Co., Ltd.
source:    南京邮电大学《数据结构A》课程实验 NOJ1048
Author:    Written by Mr.YangWenxuan
Version:   1.0
Date:      2020.05.20
Description:  二叉树(binary tree)是非常重要的树形数据结构，它是结点的有限集合，该集合或者为空集，
              或者是由一个根和两个互不相交的、称为该根的左子树和右子树的二叉树组成。
Others:   None
Function List:  main
History:  The first edition 2020.05.19
*************************************************/

#include<stdio.h>
#include<stdlib.h>
#include<math.h>
//#include<windows.h>

/* @define ElemType、Status */
#define ERROR 0       /* No error       */
#define OK 1          /* Invalid token  */
#define BOOL int      /* Expect a type  */
#define TRUE  1
#define FALSE 0
#define Overflow 2    /* 表示上溢        */
#define Underflow 3   /* 表示下溢        */
#define NotPresent 4  /* 表示元素不存在   */
#define Duplicate 5   /* 表示有重复元素   */
typedef int ElemType;
typedef int Status;

/* @struct mGraph */
typedef struct
{
	ElemType **a;
	int n;
	int e;
	ElemType noEdge;
}mGraph;

int Init(mGraph *mg, int nSize, int eNum)
{
	int i, j;
	mg->n = nSize;
	mg->e = eNum;
	mg->noEdge = 0;
	mg->a = (ElemType**)malloc(nSize * sizeof(ElemType*));
	if (!mg->a)
		return 0;
	for (i = 0;i < mg->n;i++)
	{
		mg->a[i] = (ElemType*)malloc(nSize * sizeof(ElemType));
		for (j = 0;j < mg->n;j++)
			mg->a[i][j] = mg->noEdge;
	}
	return 1;
}

//循环队列的结构体定义
typedef struct{
    int front;
    int rear;
    int maxSize;    //最大容量
    ElemType *element;
}Queue;
 
 
//创建一个能容纳mSize个单元的空队列
void Create(Queue *Q,int mSize){
    Q->maxSize=mSize;
    Q->element=(ElemType*)malloc(sizeof(ElemType)*mSize);
    Q->front=Q->rear=0;
}
 
 
//判断队列是否为空,若是,则返回TRUE;否则返回FALSE
BOOL IsEmpty(Queue *Q){
    return Q->front==Q->rear;
}
 
//判断队列是否已满,若是,则返回TRUE,否则返回FALSE
BOOL IsFULL(Queue *Q){
    return (Q->rear+1)%Q->maxSize==Q->front;
}
 
//获取队头元素,并通过x返回.若操作成功,则返回TRUE,否则返回FALSE
BOOL Front(Queue *Q,ElemType *x){
    if(IsEmpty(Q))      //空队列处理
        return FALSE;
    *x=Q->element[(Q->front+1)%Q->maxSize];
    return TRUE;
}
 
//入队.在队列Q的队尾插入元素x(入队操作)。操作成功,则返回TRUE,否则返回FALSE
BOOL EnQueue(Queue *Q,ElemType x){
    if(IsFULL(Q))      //溢出处理
        return FALSE;
    Q->rear=(Q->rear+1)%Q->maxSize;
    Q->element[Q->rear]=x;
    return TRUE;
}
 
//出队.从队列Q中删除队头元素(出队操作)。操作成功,则返回TRUE,否则返回FALSE
BOOL DeQueue(Queue *Q){
    if(IsEmpty(Q)){   //空队列处理
        return FALSE;
    }
    Q->front=(Q->front+1)%Q->maxSize;
    return TRUE;
}

int Insert(mGraph *mg, int u, int v)
{
	mg->a[u][v] = 1;
	return 1;
}

void Print(mGraph *mg)
{
	int i, j;
	for (i = 0;i < mg->n;i++)
	{
		for (j = 0;j < mg->n;j++)
			printf("%d ", mg->a[i][j]);
		printf("\n");
	}
}

void Destroy(mGraph *mg)
{
	int i;
	for (i = 0;i < mg->n;i++)
		free(mg->a[i]);
	free(mg->a);
}

void BFS(int u, mGraph mg, int visited[])
{
	 Queue q;
    Create(&q,mg.n);                        //初始化队列
    visited[u] = 1;                        //为顶点v打上访问标记
    printf("%d ",u);                       //访问顶点v
    EnQueue(&q,u);                         //将顶点v放入队列
    while(!IsEmpty(&q)){
        Front(&q,&u);
        DeQueue(&q);                       //队首顶点出队列
        for(int i = 0;i < mg.n;i ++){       //遍历v的每一项
            if(!visited[i] && mg.a[u][i] > 0){       //若未被访问且有权值,则将其访问并放入队列,注意这里判断的是g.a[v][i]二维数组
                visited[i] = 1;
                printf("%d ",i);
                EnQueue(&q,i);
            }
        }
    }
}
 


void BFSgraph(mGraph mg)
{
	int i, *visited;
	visited = (int*)malloc(sizeof(int)*mg.n);
	for (i = 0;i < mg.n;i++)
		visited[i] = 0;
	for (i = 0;i < mg.n;i++)
		if (!visited[i])
			BFS(i, mg, visited);
}

int main()
{
	mGraph graph;
	int n, e, u, v, i;
	scanf("%d%d", &n, &e);
	Init(&graph, n, e);
	for (i = 0;i < e;i++)
	{
		scanf("%d%d", &u, &v);
		Insert(&graph, u, v);
		Insert(&graph, v, u);
	}
	Print(&graph);
	BFSgraph(graph);
	Destroy(&graph);
	return 0;
}
```

[NOJ1049 飞机最少换乘次数问题](https://acm.njupt.edu.cn/problem/NOJ1049)<br>
```C++
/*************************************************
Copyright (C++), 2018-2022,Literature Tech. Co., Ltd.
source:    南京邮电大学《数据结构A》课程实验 NOJ1049
Author:    Written by Mr.YangWenxuan
Version:   1.0
Date:      2020.05.20
Description:  设有n个城市，编号为0～n-1，m条单向航线的起点和终点由输入提供，寻找一条换乘次数最少的线路方案。
Others:   None
Function List:  main
History:  The first edition 2020.05.19
*************************************************/
#include <iostream>
using namespace std;

/* @variable temp */
const int N = 20;
int minPath,n;
bool edge[N][N] = { false };
bool mask[N] = { false };

/*
 * Function:   dfs
 * Description: 从起点城市v到其他n-1个城市最少换乘次数，
                按照终点城市序号从小到大顺序排序
 * Input:    int s, int e, int count
 * Output:   None
 * Return:   None
 * Others:   None
 */
void dfs(int s, int e, int count)
{
	if (count > minPath)
		return;
	if (s == e && minPath > count)
		minPath = count;
	else
	{
		for (int i = 0; i < n; i++)
			if (edge[s][i] && !mask[i])
				dfs(i, e, count + 1);
		mask[s] = true;
	}                         
}

int main(void)
{
	int m, v;
	cin >> n >> m >> v;
	for (int i = 0; i < m; i++)
	{
		int v1, v2;
		cin >> v1 >> v2;
		edge[v1][v2] = true;
	}
	for (int i = 0; i < n; i++)
	{
		if (i != v)
		{
			minPath = 0xFFFF;
			dfs(v, i, 0);
			if (minPath == 0xFFFF)
				minPath = -1;
			cout << minPath << endl;
		}
		for (int j = 0; j < n; j++)
			mask[j] = false;
	}
	return 0;
}
```


## 实验四<br>
[NOJ1061 简单选择排序](https://acm.njupt.edu.cn/problem/NOJ1061)<br>
```C
/*************************************************
Copyright (C), 2018-2022,Literature Tech. Co., Ltd.
source:    南京邮电大学《数据结构A》课程实验 NOJ1061
Author:    Written by Mr.YangWenxuan
Version:   1.0
Date:      2020.05.20
Description:  给定输入排序元素数目n和相应的n个元素，写出程序，
              利用内排序算法中的简单选择排序算法进行排序，
              并输出排序过程中每趟及最后结果的相应序列。
Others:   None
Function List:  main
History:  The first edition 2020.05.19
*************************************************/
#include<stdio.h>
#include<stdlib.h>
int main()
{
    int n,*a,i,j;
    scanf("%d",&n);
    a=(int*)malloc(sizeof(int)*n);
    for(i=0;i<n;i++)
        scanf("%d",a+i);
    printf("Source:\n(");
    for(i=0;i<n-1;i++)
        printf("%d ",a[i]);
    printf("%d)\nSelect Sort:\n",a[i]);
    for(i=0;i<n;i++)
    {
        int temp,h; 
		int min=i;
        for(j=i+1;j<n;j++)
            if(a[j]<a[min])
                min=j;
            if(min!=i)
            {
                temp=a[i];
                a[i]=a[min];
                a[min]=temp;
            }
        if(i<n-1)
        {
            printf("(");
            for(h=0;h<i;h++)
                printf("%d ",a[h]);
            printf("%d)",a[h]);
            for(h++;h<n;h++)
                printf(" %d",a[h]);
            printf("\n");
        }
        else
        {
            printf("Result:\n(");
            for(h=0;h<n-1;h++)
                printf("%d,",a[h]);
            printf("%d)\n",a[h]);
        }
    }
    return 0;
}
```

[NOJ1062 直接插入排序](https://acm.njupt.edu.cn/problem/NOJ1062)<br>
```C
/*************************************************
Copyright (C), 2018-2022,Literature Tech. Co., Ltd.
source:    南京邮电大学《数据结构A》课程实验 NOJ1062
Author:    Written by Mr.YangWenxuan
Version:   1.0
Date:      2020.05.20
Description:  给定输入排序元素数目n和相应的n个元素，写出程序，
              利用内排序算法中直接插入排序算法进行排序，
              并输出排序过程中每趟及最后结果的相应序列。
Others:   None
Function List:  main
History:  The first edition 2020.05.19
*************************************************/

#include<stdio.h>
 /* @variable temp */
int a[400];
 
int main()
{
	int n;
	scanf("%d",&n);
	for(int i=0;i<n;i++)
		scanf("%d",&a[i]);
 
	printf("Source:\n(%d)",a[0]);
	for(int i=1;i<n;i++)
		printf(" %d",a[i]);
	printf("\nInsert Sort:\n");
 
	for(int i=1;i<n;i++)
	{
		if(a[i] < a[i-1])
		{
			int tmp = a[i], j;
			for(j=i-1;j>=0&&a[j]>tmp;j--)
				a[j+1] = a[j];
			a[j+1] = tmp;
		}
		printf("(%d",a[0]);
		for(int t=1;t<=i;t++) printf(" %d",a[t]);
		printf(")");
		for(int t=i+1;t<n;t++) printf(" %d",a[t]);
		printf("\n");
	}
	printf("Result:\n(%d",a[0]);
	for(int i=1;i<n;i++)
		printf(" %d",a[i]);
	printf(")\n");
 
	return 0;

}
```

[NOJ1063 冒泡排序](https://acm.njupt.edu.cn/problem/NOJ1063)<br>
```C
/*************************************************
Copyright (C), 2018-2022,Literature Tech. Co., Ltd.
source:    南京邮电大学《数据结构A》课程实验 NOJ1063
Author:    Written by Mr.YangWenxuan
Version:   1.0
Date:      2020.05.20
Description:  给定输入排序元素数目n和相应的n个元素，写出程序，
              利用内排序算法中冒泡排序算法进行排序，
              并输出排序过程中每趟及最后结果的相应序列。
Others:   None
Function List:  main
History:  The first edition 2020.05.19
*************************************************/

#include<stdio.h>

/* @define SWAP */
#define SWAP(x, y) {int tmp=x; x=y; y=tmp;}
 
/* @variable temp */
int a[400];
 
int main()
{
	int flag = 1;
	int n;
	scanf("%d",&n);
	for(int i=0;i<n;i++)
		scanf("%d",&a[i]);
 
	printf("Source:\n(%d",a[0]);
	for(int i=1;i<n;i++)
		printf(" %d",a[i]);
	printf(")\n");
 
	printf("Bubble Sort:\n");
 
	int i = n-1, last;
	while(i>0) // 每次最大的到后面
	{
		last = 0;
		for(int j=0;j<i;j++)
		{
			if(a[j+1]<a[j])
			{
				SWAP(a[j], a[j+1]);
				last=j;
			}   
		}     
		i=last;
 
		printf("(");
		for(int j=0;j<n-1;j++)
		{
			printf("%d",a[j]);
			if(last == j)
				printf(") ");
			else
				printf(" ");
		}
		printf("%d\n",a[n-1]);
	}
	printf("Result\n(%d",a[0]);
	for(int i=1;i<n;i++)
		printf(" %d",a[i]);
	printf(")\n");
 
	return 0;

}
```

[NOJ1064 快速排序](https://acm.njupt.edu.cn/problem/NOJ1064)<br>
```C
/*************************************************
Copyright (C), 2018-2022,Literature Tech. Co., Ltd.
source:    南京邮电大学《数据结构A》课程实验 NOJ1064
Author:    Written by Mr.YangWenxuan
Version:   1.0
Date:      2020.05.20
Description:  给定输入排序元素数目n和相应的n个元素，写出程序，
              利用内排序算法中快速排序算法进行排序，
              并输出排序最后结果的相应序列。
Others:   None
Function List:  main
History:  The first edition 2020.05.19
*************************************************/
#include<stdio.h>
#include<stdlib.h>

void Swap(int a[],int i,int j)
{
	int temp=a[i];
	a[i]=a[j];
	a[j]=temp;
}
//分割函数
int Part(int a[],int low,int high)
{
	int i,j,x;
    i=low;
	j=high+1;
	x=a[low];
	do
	{
		do i++;while(a[i]<x);   //i前进
		do j--;while(a[j]>x);   //j前进
		if(i<j)
			Swap(a,i,j);
	}while(i<j);
	Swap(a,low,j);
	return j;                  //j为分割元素下标
}
void QuickSort1(int a[],int low,int high,int n)
{
	int m,q;
	if(low<high)             //当前序列至少两个元素
	{
		m=Part(a,low,high);
        QuickSort1( a,low,m-1, n);
        QuickSort1( a,m+1,high, n);
	}
}
void QuickSort2(int a[],int n)
{
	int k,p;
	QuickSort1(a,0,n-1,n);
}

int main()
{
    int n,*a,i,j,h;
    scanf("%d",&n);
    a=(int*)malloc(sizeof(int)*n);
    for(i=0;i<n;i++)
        scanf("%d",a+i);
    QuickSort2(a,n);
    for(h=0;h<n-1;h++)
       printf("%d ",a[h]);
    printf("%d\n",a[h]);
    return 0;
}
```

[NOJ1065 两路合并](https://acm.njupt.edu.cn/problem/NOJ1065)<br>
```C++
/*************************************************
Copyright (C++), 2018-2022,Literature Tech. Co., Ltd.
source:    南京邮电大学《数据结构A》课程实验 NOJ1065
Author:    Written by Mr.YangWenxuan
Version:   1.0
Date:      2020.05.20
Description:  给定输入排序元素数目n和相应的n个元素，写出程序，
              利用内排序算法中两路合并排序算法进行排序，
              并输出排序最后结果的相应序列。
Others:   None
Function List:  main
History:  The first edition 2020.05.19
*************************************************/

#include<stdio.h>
/* @variable temp */
int a[100000];
  
void merge(int a[], int i1, int j1, int i2, int j2)
{
	int i = i1;int j = i2;
	int *tmp = new int[j2-i1+1];
	int k = 0;
	while(i <= j1 && j <= j2)
	{
		if(a[i] <= a[j])
			tmp[k++] = a[i++];
		else
			tmp[k++] = a[j++];
	}
	while(i <= j1)
		tmp[k++] = a[i++];
	while(j <= j2)
		tmp[k++] = a[j++];
	for(int i=0;i<k;i++)
		a[i1++] = tmp[i];
	delete tmp;
}
 
void mergesort(int a[], int n)
{
	int i1, j1, i2, j2; // i1,j1是子序列1的下、上界；i2、j2是子序列2的下、上界
	int size = 1;
	while(size < n)
	{
		i1 = 0;
		while(i1+size < n) // 存在2个子序列
		{
			i2 = i1+size;
			j1 = i2-1;
			if(i2+size-1 > n-1) // 第2个子序列中不足size个元素
				j2 = n-1;
			else 
				j2 = i2+size-1; // 第2个子序列中有size个元素
			merge(a, i1, j1, i2, j2); // 合并相邻两个子序列
			i1 = j2+1; // 确定下一次合并第1个子序列的下界
		}
		size *= 2; // 元素个数扩大一倍
	}
}
 
int main()
{
	int n;
	scanf("%d",&n);
	for(int i=0;i<n;i++)
		scanf("%d",&a[i]);
	mergesort(a, n);
	for(int i=0;i<n-1;i++)
		printf("%d ",a[i]);
	printf("%d\n",a[n-1]);
	return 0;

}
```

[NOJ1066 堆排序](https://acm.njupt.edu.cn/problem/NOJ1066)<br>
```C
/*************************************************
Copyright (C), 2018-2022,Literature Tech. Co., Ltd.
source:    南京邮电大学《数据结构A》课程实验 NOJ1066
Author:    Written by Mr.YangWenxuan
Version:   1.0
Date:      2020.05.20
Description:  给定输入排序元素数目n和相应的n个元素，写出程序，
              利用内排序算法中堆排序算法进行排序，
              并输出排序最后结果的相应序列。
Others:   None
Function List:  main
History:  The first edition 2020.05.19
*************************************************/

#include<stdio.h>
/* @define SWAP */
#define SWAP(x, y) {int tmp=x; x=y; y=tmp;}
/* @variable temp */
int a[100000];
 
void AdjustDown(int a[], int r, int j)
{
	int child = 2*r+1;
	int tmp = a[r];
	while(child <= j)
	{
		if(child < j && a[child] < a[child+1]) child ++;
		if(tmp >= a[child]) break;
		a[(child-1)/2] = a[child];
		child = 2*child+1;
	}
	a[(child-1)/2] = tmp;
}
 
void heapsort(int a[], int n)
{
	for(int i=(n-2)/2;i>-1;i--) AdjustDown(a, i, n-1); // 构造最大堆
	for(int i=n-1;i>0;i--)
	{
		SWAP(a[0], a[i]); // 大的到屁股后面去
		AdjustDown(a, 0, i-1);
	}
}
 
int main()
{
	int n;
	scanf("%d",&n);
	for(int i=0;i<n;i++)
		scanf("%d",&a[i]);
	heapsort(a, n);
	for(int i=0;i<n-1;i++)
		printf("%d ",a[i]);
	printf("%d\n",a[n-1]);
	return 0;
}
```



