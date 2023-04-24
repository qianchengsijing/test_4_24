# test_4_24
#define _CRT_SECURE_NO_WARNINGS  1

#include <stdio.h>
顺序表的静态分配
#define MaxSize 50  
typedef struct
{
	int data[MaxSize];
	int length;
}sqlist;
void Initlist(sqlist &L）
{
	int i = 0;
	for(i=0;i<MaxSize;i++)
		L.data[i] = 0;
	L.length = 0;
}
void Initlist(sqlist &L）
{
	L.length = 0;
}
int GetElem(sqlist &L,int i)
{
	for(i=0;i<L.length;i++)
		printf("data[i]=%d\n",i,L.data[i]);
	return 1;
}
int main()
{
	int i = 0;
	sqlist L;
	Initlist(L);
	for(i=0;i<MaxSize;i++)
		printf("data[%d]=%d\n",i,L.data[i]);
	return 0;
}
int main()
{
	int i = 0;
	sqlist L;
	Initlist(L);
	int ret = GetElem(L,i);
	printf("%d\n",ret);
	return 0;
}
顺序表的动态分配
#include <stdlib.h>
#define initsize 10
typedef struct
{
	int* data;
	int MaxSize;
	int length;
}seqlist;
void Initlist(seqlist &L)
{
	L.data=(int*)malloc(initsize*sizeof(int));
	L.length=0;
	L.MaxSize = initsize;
}
void IncreaseSize(seqlist &L,int len)
{
	int i = 0;
	int* p = L.data;
	L.data=(int*)malloc((L.MaxSize+len)*sizeof(int));
	for(i=0;i<L.length;i++)
		L.data[i] = p[i];
	L.MaxSize = L.MaxSize + len;
	free(p);
}
int main()
{
	seqlist L;
	Initlist(L);
	IncreaseSize(L,5);
	return 0;
}

#define InitSize 10
typedef struct 
{
	Elemtype* data;
	int MaxSize;
	int length;
}seqlist;
//顺序表的按位查找
Elemtype GetElem(seqlist L,int i)
{
	return L.data[i-1];
}
//顺序表的按值查找
Elemtype LocateElem(seqlist L,Elemtype e)
{
	for(int i = 0;i<L.length;i++)
	{
		if(L.data[i] == e)
			return i+1;
	}
}
int main()
{
	seqlist L;
	InitSize(L);
	GetElem(L,i);
	return 0;
}
结构体的比较
typedef struct
{
	int num;
	int people;
}customer;
bool iscustomerequal(customer a,customer b)
{
	if(a.num == b.num && a.people == b.people)//或者调用函数
		//	printf("相等\n");
	//else
	//	printf("不相等\n");
}
void test()
{
	customer a;
	a.num = 1;
	a.num = 1;
	customer b;
	b.num = 1;
	b.num = 1;
	if(a == b)//结构体不能直接比较，需比较各个分量来比较
		printf("相等\n");
	else
		printf("不相等\n");
	if(a.num == b.num && a.people == b.people)//或者调用函数
		//	printf("相等\n");
	//else
	//	printf("不相等\n");
}
顺序表的插入
#define MaxSize 10
typedef struct
{
	int data[MaxSize];
	int length;
}sqlist;
void Initlist(sqlist &L)
{
	int i = 0;
	for(i=0;i<L.length;i++)
	{
		L.data[i] = 0;
	}
	L.length = 0;
}
bool ListInsert(sqlist &L,int i,int e)
{
	int j = 0;
	if(i<1 || i>L.length+1)
		return false;
    if(L.length>=MaxSize)
		return false;
	for(j=L.length;j>=i;j--)
		L.data[j] = L.data[j-1];
	L.data[i-1] = e;
	L.length++;
	return true;
}
int main()
{
	sqlist L={1,2,3,5,6,7,8,9,10};
	Initlist(L);
	ListInsert(&L,4,4);
	return 0;
}
顺序表的删除
bool Deletelist(sqlist &L,int i,int &e)
{
	int j = 0;
	if(i<1 || i>L.length)
		return false;
	e = L.data[i-1];
	for(j=i;j<L.length;j++)
		L.data[j-1] = L.data[j];
	L.length--;
	return true;
}
int main()
{
	sqlist L;
	Initlist(L);
	int e = -1;
	if(Deletelist(&L,3,e));
	    printf("已删除第三个元素");
	else
		printf("位序不合法")
	return 0;
}
#include <stdlib.h>
struct LNode* p = (struct LNode*)malloc(sizeof(struct LNode));
单链表的实现
typedef struct LNode
{
	Elemtype data;
	struct LNode* next;
}LNode,*Linklist;
不带头结点
bool Initlist(Linklist &L)
{
	L = NULL;
	return true;
}
void test()
{
	Linklist L;//声明一个指向单链表的指针
	Initlist(L);
}
带头结点
bool Initlist(Linklist &L)
{
	L = (LNode*)malloc(sizeof(LNode));//动态分配一个结点
	if(L == NULL)
		return false;
	L->next = NULL;
	return true;
}
判断单链表是否为空
bool Empty(Linklist L)
{
	if(L->next == NULL)
		return true;
}
#define _CRT_SECURE_NO_WARNINGS  1
#include <stdio.h>
#include <stdlib.h>
typedef struct LNode
{
	int data;
	struct LNode* next;
}LNode,*Linklist;
单链表的插入
按位序插入（带头结点）
bool ListInsert(Linklist &L,int i,int e)
{
	if(i<1)
		return false;
	LNode* p;
	int j =0;
	p = L;
	while(p != NULL && j<i-1)
	{
		p = p->next;
	    j++;
	}
	if(p = NULL)
		return false;
	LNode* s = (LNode*)malloc(sizeof(LNode));
	s->data = e;
	s->next = p->next;
	p->next = s;
	return true;
}
不带头结点
bool ListInsert(Linklist &L,int i,int e)
{
	if(i<1)
		return false;
	if(i == 1)
	{
		LNode* s = (LNode*)malloc(sizeof(LNode));
		s->data = e;
		s->next = L;
		L = s;
		return true;
	}
	LNode* p;
	int j =1;//此时P指向第一个结点
	p = L;
	while(p != NULL && j<i-1)
	{
		p = p->next;
	    j++;
	}
	if(p = NULL)
		return false;
	LNode* s = (LNode*)malloc(sizeof(LNode));
	s->data = e;
	s->next = p->next;
	p->next = s;
	return true;
}
指定结点后插
bool InsertNextNode(LNode* p,int e)
{
	if(p == NULL)
		return false;
	LNode* s = (LNode*)malloc(sizeof(LNode));
	if(s == NULL)//判断内存是否不足
		return false;
	s->data = e;
	s->next = p->next;
	p->next = s;
	return true;
}
指定结点前插
bool InsertPirorNode(LNode* p,int e)
{
	if(p == NULL)
		return false;
	LNode* s = (LNode*)malloc(sizeof(LNode));
	if(s == NULL)//判断内存是否不足
		return false;
	s->next = p->next;
	p->next = s;
	s->data = p->data;
	p->data = e;
	return true;
}
王道书上算法
bool InsertPirorNode(LNode* p,LNode* s)
{
	if(p == NULL || s == NULL)
		return false;
	s->next = p->next;
	p->next = s;
	int temp = p->data;
	p->data = s->data;
	s->data = temp;
	return true;
}
int main()
{
	Linklist L;
	Initlist(L);
	ListInsert(&L,i,e);
	return 0;
}
按位序删除（带头结点）
bool ListDelete(Linklist &L,int i,int &e)
{
	if(i<1)
		return false;
	LNode* p;
	int j = 0;
	p = L;
	while(p != NULL && j<i-1)
	{
		p = p->next;
	    j++;
	}
	if(p == NULL)
		return false;
	if(p->next == NULL)
		return false;
	LNode* s = p->next;
	e = s->data;
	p->next = s->next;
	free(s);
	return true;
}
int main()
{
	Linklist L;
	Initlist(L);
	ListDelete(L,i,e);
	return 0;
}
#include <stdio.h>
#include <stdlib.h>
typedef struct LNode
{
	int data;
	struct LNode* next;
}LNode,*Linklist;
bool Initlist(Linklist &L)
{
	L = (LNode*)malloc(sizeof(LNode));
	if(L == NULL)
		return false;
	L->next = NULL;
	return true;
}
//单链表的删除
//按位序删除（带头结点）
bool ListDelete(Linklist &L,int i,int &e)
{
	if(i<1)
		return false;
	LNode* p;
	int j = 0;
	p = L;
	while(p != NULL && j<i-1)
	{
		p = p->next;
		j++;
	}
	if(p == NULL)
		return false;
	if(p->next == NULL)
		return false;
	LNode* q = p->next;
	e = q->data;
	p->next = q->next;
	free(q);
	return true;
}
//按位序删除（不带头结点）
bool ListDelete(Linklist &L,int i,int &e)
{
	if(i<1)
		return false;
	if(i == 1)
	{
		LNode* s = L;
		e = s->data;
		L = s->next;
		free(s);
		return true;
	}
	LNode* p;
	int j = 1;
	p = L;
	while(p != NULL && j<i-1)
	{
		p = p->next;
		j++;
	}
	if(p == NULL)
		return false;
	if(p->next == NULL)
		return false;
	LNode* q = p->next;
	e = q->data;
	p->next = q->next;
	free(q);
	return true;
}
//删除指定结点（带头结点）
bool DeleteNode(LNode* p)
{
	if(p == NULL)
		return false;
	LNode* q = p->next;
	p->data = p->next->data;
	p->next = q->next;
	free(q);
	return true;
}
//如果删除的为最后一个元素，则要从头遍历
//按位查找
bool GetElem(Linklist L,int i)
{
	if(i<1)
		return false;
	LNode* p;
	int j = 0;
	p = L;
	while(p != NULL && j<i)
	{
		p = p->next;
		j++;
	}
	return p;
}
//按值查找
bool LocateElem(Linklist L,int e)
{
	LNode* p = L->next;
	while(p != NULL && p->data != e)
		p = p->next;
	return p;
}
//求表的长度(带头结点）
int length(Linklist L)
{
	int len = 0;
	LNode* p = L;//不带头结点时,设int len = 1;
	while(p->next != NULL)
	{
		p = p->next;
		len++;
	}
	return len;
}
//单链表的建立（尾插法）（带头结点）
Linklist List_TailInsert(Linklist &L)//正向建立单链表
{
	int x = 0;
	L = (LNode*)malloc(sizeof(LNode));//建立头结点；
	LNode* s,*r = L;
	scanf("%d",&x);
	while(x != 9999)
	{
	    s = (LNode*)malloc(sizeof(LNode));
		s->data = x;
		r->next = s;
		r = s;
		scanf("%d",&x);
	}
	r->next = NULL;
	return L;
}
//单链表的头插法（带头结点）
Linklist List_HeadInsert(Linklist &L)//逆向建立单链表
{
	LNode* s;
	int x;
	L = (LNode*)malloc(sizeof(LNode));
	L->next = NULL;
	scanf("%d",&x);
	while(x != 9999)
	{
		s = (LNode*)malloc(sizeof(LNode));
		s->data = x;
		s->next = L->next;
		L->next = s;
		scanf("%d",&x);
	}
	return L;
}
Linklist List_HeadInsert(Linklist &L)
{
	LNode* s;
	int x;
	L = NULL;
	scanf("%d",&x);
	while(x != 9999)
	{
		s = (LNode*)malloc(sizeof(LNode));
		s->data = x;
		s->next = L;
		L = s;
		scanf("%d",&x);
	}
	return L;
}
int main()
{
	Linklist L;
	Initlist(L);
	ListDelete(&L,i,&e);
	DeleteNode(p);
	return 0;
}
