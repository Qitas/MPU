.. _lan_c_list:

链表
===============


.. contents::
    :local:
    :depth: 1

单向链表
-----------

.. code-block:: bash

    typedef int SLTDateType;
    typedef struct SListNode
    {
        SLTDateType data;
        struct SListNode* next;
    }SListNode;

无头+单向+非循环链表增删查改实现

.. code-block:: bash

    SListNode* BuySListNode(SLTDateType x)
    {
        SListNode* tmp = (SListNode*)malloc(sizeof(SListNode));
        if (tmp == NULL){
            printf("无法给节点开辟空间\n");
            return NULL;
        }
        else{
            tmp->data = x;
            tmp->next = NULL;
            return tmp;
        }
    }

单链表尾插入和删除

.. code-block:: bash

    void SListPushBack(SListNode** pplist, SLTDateType x)
    {

        SListNode* newnode = BuySListNode(x);
        if ( *pplist== NULL){
            *pplist = newnode;
        }
        else{
            SListNode* tail = *pplist;
            while (tail->next != NULL){
                tail = tail->next;
            }
            tail->next = newnode;
        }
    }
    void SListPopBack(SListNode** pplist)
    {
        assert(*pplist);
        SListNode* cur = *pplist;
        SListNode* prev = NULL;
        if (cur->next == NULL){
            free(cur);
            *pplist = NULL;
        }
        else{
            while (cur->next != NULL){
                prev = cur;
                cur = cur->next;
            }
            free(cur);
            prev->next = NULL;
        }
    }


单链表打印输出和查找

.. code-block:: bash

    void SListPrint(SListNode* plist)
    {
        SListNode* head = plist;
        while (head != NULL){
            printf("%d ", head->data);
            head = head->next;
        }
    }
    SListNode* SListFind(SListNode* plist, SLTDateType x)
    {
        assert(plist);
        while (plist != NULL)
        {
            if (plist->data == x)
            {
                return plist;
            }
            plist = plist->next;
        }
        return NULL;
    }



双向链表
-----------

.. code-block:: bash

    typedef int LTDataType;
    typedef struct ListNode
    {
        ListDateType val;
        struct ListNode* prev;
        struct ListNode* next;
    }ListNode;


创建返回链表的头结点

.. code-block:: bash

    ListNode* BuyList(ListDateType x)
    {
        ListNode* newnode = (ListNode*)malloc(sizeof(ListNode));
        if (newnode == NULL){
            printf("BuyList fail\n");
            exit(-1);
        }
        newnode->val = x;
        newnode->next = NULL;
        newnode->prev = NULL;
        return newnode;
    }

在双向链表尾插入和删除

.. code-block:: bash

    void ListPushBack(ListNode* phead, ListDateType x)
    {
        assert(phead);
        ListNode* newnode = BuyList(x);
        ListNode* tail = phead->prev;
        tail->next = newnode;
        phead->prev = newnode;
        newnode->next = phead;
        newnode->prev = tail;
    }
    void ListPopBack(ListNode* phead)
    {
        assert(phead->next != phead);
        ListNode* tail = phead->prev;
        ListNode* prev = tail->prev;
        phead->prev = prev;
        prev->next = phead;
        free(tail);
        tail = NULL;
    }

在双向链表头插入和删除

.. code-block:: bash

    void ListPushFront(ListNode* phead, ListDateType x)
    {
        assert(phead);
        ListNode* newnode = BuyList(x);
        ListNode* head = phead->next;
        phead->next = newnode;
        head->prev = newnode;
        newnode->next = head;
        newnode->prev = phead;
    }
    void ListPopFront(ListNode* phead)
    {
        assert(phead);
        assert(phead->next != phead);
        ListNode* head = phead->next;
        ListNode* next = head->next;
        phead->next = next;
        next->prev = phead;
        free(head);
        head = NULL;
    }

在pos之前插入和删除

.. code-block:: bash

    void ListInsert(ListNode* pos, ListDateType x)
    {
        assert(pos);
        ListNode* newnode = BuyList(x);
        ListNode* prev = pos->prev;
        prev->next = newnode;
        pos->prev = newnode;
        newnode->prev = prev;
        newnode->next = pos;
    }
    void ListErase(ListNode* pos)
    {
        assert(pos);
        ListNode* prev = pos->prev;
        ListNode* next = pos->next;
        prev->next = next;
        next->prev = prev;
        free(pos);
        pos = NULL;
    }
