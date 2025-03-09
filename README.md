# Stack
#include <iostream>
using namespace std;
class Node
{
private:
    int object;
    Node *nextNode;

public:
    Node() : object(0), nextNode(nullptr) {}
    Node(int val)
    {
        object = val;
        nextNode = nullptr;
    }
    int get() const { return object; }
    void set(int object) { this->object = object; }
    Node *getNext() { return nextNode; }
    void setNext(Node *nextNode) { this->nextNode = nextNode; }
};

class Linkedlist
{
    Node *head;
    int size;

public:
    Linkedlist()
    {
        head = nullptr;
        size = 0;
    }
    Linkedlist(int val)
    {
        Node *newNode = new Node(val);
        head = newNode;
        size = 1;
    }
    void add(int val)
    {
        Node *newNode = new Node(val);
        newNode->setNext(head);
        head = newNode;
        size++;
    }
    void display()
    {
        Node *temp = head;
        while (temp != nullptr)
        {
            cout << temp->get() << " -> ";
            temp = temp->getNext();
        }
        cout << "NULL" << endl;
    }
    int remove()
    {
        if (head == nullptr)
        {
            cout << "Stack Empty" << endl;
            return -1;
        }
        Node *temp = head;
        head = head->getNext();
        int poppedValue = temp->get();
        delete temp;
        size--;
        return poppedValue;
    }
    int sizeList()
    {
        return size;
    }
    int topValue()
    {
        if (head == nullptr)
        {
            cout << "Stack is empty!" << endl;
            return -1;
        }
        return head->get();
    }
};
class Stack
{
private:
    Linkedlist l;

public:
    Stack()
    {
    }
    void push(int val)
    {
        l.add(val);
    }
    int pop()
    {
        return l.remove();
    }
    int size()
    {
        return l.sizeList();
    }
    int top()
    {
        return l.topValue();
    }
    void display()
    {
        l.display();
    }
};
int main()
{
    Stack s;
    s.push(1);
    s.push(2);
    s.push(3);
    cout << s.pop() << endl;
    cout << s.top() << endl;
    cout << s.size() << endl;
    s.display();
}
