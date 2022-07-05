#include <iostream>
#include <string.h>
using namespace std;
struct abc {

	int data;
	abc* next;
	abc* prev;

};
abc* head = NULL;
void insert_at_Front() {
	abc* p = new abc;
	cout << "Enter a data: ";
	cin >> p->data;
	p->next = NULL;
	p->prev = NULL;
	if (head == NULL) {
		head = p;
	}
	else {
		head->prev = p;
		p->next = head;
		head = p;
	}

}
void insert_at_Middle() {
	abc* p = new abc;
	cout << "Enter a data: ";
	cin >> p->data;
	p->next = NULL;
	p->prev = NULL;
	abc* Aglaptr = head;
	abc* Pichlaptr = NULL;
	while (Aglaptr != NULL && p->data > Aglaptr->data) {
		Pichlaptr = Aglaptr;
		Aglaptr = Aglaptr->next;

	}
	if (Pichlaptr == NULL) {
		p->next = head;
		head = p;
	}
	else if (Aglaptr == NULL) {
		Pichlaptr->next = p;
		p->prev = Pichlaptr;
	}
	else {
		Pichlaptr->next = p;
		p->next = Aglaptr;
		p->prev = Pichlaptr;
		Aglaptr->prev = p;
	}
}

void insert_after() {
	int x;
	abc* p = new abc;
	abc* temp = head;
	cout << "Enter the data you want to store the digit after: " << endl;
	cin >> x;
	cout << "Enter the vlue to store: " << endl;
	cin >> p->data;

	p->next = NULL;
	p->prev = NULL;

	abc* Aglaptr = temp->next;
	abc* Pichlaptr = temp;
	while (temp != NULL) {


		if (x == temp->data) {



			temp->next = p;
			//p = temp;
			p->prev = Pichlaptr;
			Pichlaptr->next = p;
			//	temp = Pichlaptr;
			p->next = Aglaptr;
			Aglaptr->prev = p;
			break;
		}
		temp = temp->next;
	}

}
void insert_before() {
	int x;
	abc* p = new abc;
	abc* temp = head;
	cout << "Enter the data you want to store the digit before: " << endl;
	cin >> x;
	cout << "Enter the vlue to store: " << endl;
	cin >> p->data;

	p->next = NULL;
	p->prev = NULL;

	abc* Aglaptr = temp->next;
	abc* Pichlaptr = temp;
	while (temp != NULL) {


		if (x == temp->data) {



			temp->prev = p;
			//p = temp;
			p->next = temp;
			Pichlaptr->next = p;
			//	temp = Pichlaptr;
			p->next = Aglaptr;
			Aglaptr->prev = p;
			break;
		}
		temp = temp->next;
	}
}

void insert_at_End() {
	abc* p = new abc;
	cout << "Enter a data: ";
	cin >> p->data;
	p->next = NULL;
	p->prev = NULL;
	if (head == NULL) {
		head = p;
	}
	else {
		abc* temp = head;
		while (temp->next != NULL) {
			temp = temp->next;
		}
		temp->next = p;
		p->prev = temp;
	}
}

void Deletion() {
	int x;
	cout << "Enter the value you want to Delete:  ";
	cin >> x;
	abc* Aglaptr = head;
	abc* Pichlaptr = NULL;
	if (head == NULL) {
		cout << "List is empty: " << endl;
	}
	else {
		while (Aglaptr != NULL && x != Aglaptr->data) {
			Pichlaptr = Aglaptr;
			Aglaptr = Aglaptr->next;
		}
		if (Pichlaptr == NULL) {
			head = head->next;
			head->prev = NULL;
			delete Aglaptr;
		}
		else if (Aglaptr == NULL) {
			cout << "Data not found" << endl;
		}
		else if (Aglaptr->next == NULL) {
			Aglaptr->next = NULL;
			delete Aglaptr;
		}

		else {
			Pichlaptr->next = Aglaptr->next;
			Aglaptr->next->prev = Pichlaptr;
			delete Aglaptr;
		}

	}

}
abc* Search() {
	int x;
	abc* p = new abc;
	abc* temp = head;
	cout << "Which element to Searh:    ";
	cin >> x;
	while (temp != NULL) {
		if (x == p->data) {
			return temp;
		}
		else {
			cout << "Not found" << endl;
		}
	}

}


void Display() {

	abc* temp = head;
	while (temp != NULL) {
		cout << temp->data << "  ";
		temp = temp->next;
	}
}
/*void Reverse_Display() {

	abc* temp = head;
	while (temp != NULL) {

		temp = temp->next;
	}
	while (temp != NULL) {
		cout << temp->data << "  ";
		temp = temp->prev;
	}
}*/

void reverseList() {
	if (head != NULL) {
		abc* prevNode = head;
		abc* tempNode = head;
		abc* curNode = head->next;

		prevNode->next = NULL;
		prevNode->prev = NULL;

		while (curNode != NULL) {
			tempNode = curNode->next;
			curNode->next = prevNode;
			prevNode->prev = curNode;
			prevNode = curNode;
			curNode = tempNode;
		}

		head = prevNode;
	}
	abc* temp = head;
	if (temp != NULL) {
		cout << "The list contains: ";
		while (temp != NULL) {
			cout << temp->data << " ";
			temp = temp->next;
		}
		cout << "\n";
	}
	else {
		cout << "The list is empty.\n";
	}
}
int main() {
	int opt, cont;
	do {
		cout << "Press <1> to insert at front" << endl;
		cout << "Press <2> to insert at middle" << endl;
		cout << "Press <3> to insert at end" << endl;
		cout << "Press <4> to Deletion" << endl;
		cout << "Press <5> to Search" << endl;
		cout << "Press <6> to Display" << endl;
		cout << "Press <7> to Reverse Display" << endl;
		cout << "Press <8> to insert after a node" << endl;
		cout << "Press <9> to insert before a node" << endl;
		cin >> opt;

		switch (opt)
		{
		case 1:
			insert_at_Front();
			break;
		case 2:
			insert_at_Middle();
			break;
		case 3:
			insert_at_End();
			break;
		case 4:
			Deletion();
			break;
		case 5:
			Search();
			break;
		case 6:
			Display();
			break;
		case 7:
			//Reverse_Display();
			reverseList();
			break;
		case 8:
			insert_after();
			break;
		case 9:
			insert_before();
			break;
		default:
			break;
		}
		cout << "Press 1 to continue: " << endl;
		cin >> cont;
	} while (cont == 1);




	return 0;
}
//////////////////////////////////Recursion//////////////////////////////////////
#include <iostream>
using namespace std;
void print_array(int arr[], int size)
{
	static int i;
	if (i == size)
		return;
	cout << arr[i] << " ";
	i++;
	print_array(arr, size);
}
void print_reverse(int arr[], int size)
{
	if (size == 0)
		return;
	size--;
	cout << arr[size] << " ";
	print_reverse(arr, size);
}
int main()
{
	int arr[10], n = 10;
	cout << "Enter 10 Numbers in Array:\n";
	for (int i = 0; i < 10; i++)
		cin >> arr[i];
	cout << "Print in Straight order: ";
	print_array(arr, n);
	cout << endl;
	cout << "Print in Reverse order: ";
	print_reverse(arr, n);
	return 0;
}
//-----------------------------------------------------------------//
#include<iostream>
using namespace std;
bool isPrime(int n, int i = 2)
{
	if (n <= 2)
		return (n == 2);
	if (n % i == 0)
		return false;
	if (i * i > n)
		return true;
	return isPrime(n, i + 1);
}
int main()
{
	int n;
	cout << "Enter a Number: ";
	cin >> n;
	if (isPrime(n))
		cout << "Number is Prime";
	else
		cout << "Number is not Prime";
	return 0;
}
//-------------------------------------------------------------------//
#include<iostream>
using namespace std;
void odd(int x, int y);
int main()
{
	int a1, a2;
	cout << "Enter 1st number\n";
	cin >> a1;
	cout << "Enter 2nd  number\n";
	cin >> a2;
	cout << "Odd numbers between 1st and 2nd number are: ";
	odd(a1, a2);
	return 0;
}
void odd(int x, int y)
{
	if (x == y)
		return;
	x = x + 1;
	if (x % 2 == 1)
		cout << x << " ";
	odd(x, y);
}
//---------------------------------------------------------------------//
#include<iostream>
using namespace std;
int palindrome_check(string s, int st, int e)
{
	if (e - st == 1 || st == e)
		return 1;
	else
	{
		if (s[st] == s[e])
			return palindrome_check(s, st + 1, e - 1);
		else
			return 0;
	}
}
int main()
{
	string s;
	cout << "Enter a String: ";
	cin >> s;
	int n = s.length();
	if (palindrome_check(s, 0, n - 1))
		cout << "String is Palandrome.";
	else
		cout << "String is not Palandrome.";
	return 0;
}
////////////////////////BST///////////////////////////////////////
#include <iostream>
using namespace std;
struct BST {
	int data;
	BST* right;
	BST* left;
};

BST* root = NULL;

BST* createNode(int data) {
	BST* p = new BST;
	p->data = data;
	p->left = NULL;
	p->right = NULL;
	return p;
}

BST* BST_insert(BST*& root, int data) {


	if (root == NULL) {
		root = createNode(data);
	}
	else if (data < root->data) {
		BST_insert(root->left, data);
	}
	else  if (data > root->data) {
		BST_insert(root->right, data);
	}
	return root;
}

BST* minimum(BST* root) {
	while (root->left != NULL) {
		root = root->left;
	}
	return root;
}

// find the node with the maximum key
BST* maximum(BST* root) {
	while (root->right != NULL) {
		root = root->right;
	}
	return root;
}


int  Height(BST*& root) {
	if (root == NULL) {
		return false;
	}
	else {
		int left_height, right_height;
		left_height = Height(root->left);
		right_height = Height(root->right);
		if (left_height > right_height) {
			return (left_height + 1);
		}
		else {
			return (right_height + 1);
		}
	}
}

void Deletion(BST*& root, int num) {


	// search the key
	if (root == NULL)
	{
		return;
	}
	else if (num < root->data) {
		Deletion(root->left, num);
	}
	else if (num > root->data) {
		Deletion(root->right, num);
	}
	else {
		// the key has been found, now delete it

		// case 1: node is a leaf node
		if (root->left == NULL && root->right == NULL) {
			delete root;
			root = NULL;
		}

		// case 2: node has only one child
		else if (root->left == NULL) {
			BST* temp = root;
			root = root->right;
			delete temp;
		}

		else if (root->right == NULL) {
			BST* temp = root;
			root = root->left;
			delete temp;
		}

		// case 3: has both children
		else {
			BST* temp = minimum(root->right);
			root->data = temp->data;
			Deletion(root->right, temp->data);
		}

	}
}


BST* Search(BST* root, int key) {
	if (root == NULL || root->data == key) {

		return root;
	}
	// Key is greater than root's data
	if (root->data < key) {

		return Search(root->right, key);
	}
	else {
		// Key is smaller than root's data
		return Search(root->left, key);
	}
}


//Indorder traversal
void inorder(BST*& root) {
	if (root == NULL) {

		return;
	}
	inorder(root->left);
	cout << root->data << " ";
	inorder(root->right);
}

//Preorder traversal
void Preorder(BST*& root)
{
	if (root == NULL) {
		return;
	}
	cout << root->data << " ";
	Preorder(root->left);
	Preorder(root->right);
}

void Postorder(BST*& root)
{
	if (root == NULL) {
		return;
	}
	Postorder(root->left);
	cout << root->data << " ";
	Postorder(root->right);
}







int main() {
	int choice;
	int option, opt;

	do {
		cout << "Press 1 to insert" << endl;
		cout << "Press 2 to Delete" << endl;
		cout << "Press 3 to Search" << endl;
		cout << "Press 4 to Display" << endl;
		cout << "Press 5 to know height of tree" << endl;
		cin >> opt;
		switch (opt) {
		case 1:
			cout << "Enter Data you want to store :\n";
			int data;
			cin >> data;
			BST_insert(root, data);

			break;

		case 2:
			int num;
			cout << "Enter the value you want to delete: " << endl;
			cin >> num;
			Deletion(root, num);
			break;

		case 3:
			int val;
			cout << "Enter value you want to search: ";
			cin >> val;
			if (Search(root, val) == 0)
				cout << "Data can't be found" << endl;
			else
				cout << "Data Exist" << endl;
			break;

		case 4:
			int opt;
			cout << "Press  1 for preorder display" << endl;
			cout << "Press 2 for inorder display" << endl;
			cout << "Press 3 for post Order display" << endl;
			cin >> opt;
			switch (opt) {
			case 1:
				Preorder(root);
				break;
			case 2:
				inorder(root);
				break;
			case 3:
				Postorder(root);
				break;
			default:
				break;

			}
			break;

		case 5:
			cout << "Height of tree is: " << endl;
			cout << Height(root);
			cout << endl;

		}
		cout << "DO you want to continue? Press <1> to do so" << endl;
		cin >> choice;

	} while (choice == 1);
}
////////////////////////////////////Min Heapify///////////////////////////////////
#include <iostream>
using namespace std;
void min_heapify(int* a, int i, int n)
{
	int j, temp;
	temp = a[i];
	j = 2 * i;
	while (j <= n)
	{
		if (j < n && a[j + 1] < a[j])
			j = j + 1;
		if (temp < a[j])
			break;
		else if (temp >= a[j])
		{
			a[j / 2] = a[j];
			j = 2 * j;
		}
	}
	a[j / 2] = temp;
	return;
}
void insert(int* a, int n)
{
	int i;
	for (i = n / 2; i >= 1; i--)
	{
		min_heapify(a, i, n);
	}
}
void display(int a[], int n)
{
	a[n];
	for (int i = 1; i <= n; i++)
	{
		cout << a[i] << endl;
	}
}

void findMin(int a[], int n)
{
	cout << "\nMinimum Number : " << a[0];
}

void deletion(int a[], int& n)
{
	swap(a[0], a[n - 1]);
	n = n - 1;
	min_heapify(a, n, 0);
	cout << "\nNumber deleted";
}

int main()
{
	int n;
	int i, x, op;
	cout << "Enter no of elements of array\n";
	cin >> n;
	int a[20];

	do
	{
		cout << "\nPress 1 to insert";
		cout << "\nPress 2 to display";
		cout << "\nPress 3 to find minimum value";
		cout << "\nPress 4 to delete";
		cout << "\n\nSelect : ";
		cin >> op;
		if (op == 1)
		{
			for (i = 1; i <= n; i++)
			{
				cout << "enter element" << (i) << endl;
				cin >> a[i];
			}
			insert(a, n);
		}
		else if (op == 2)
		{
			display(a, n);
		}
		else if (op == 3)
		{
			findMin(a, n);
		}
		else if (op == 3)
		{
			deletion(a, n);
		}
	} while (op == 1 || op == 2 || op == 3 || op == 4);

}
//------------------------------------------------------------------------//
#include <iostream>
using namespace std;
void max_heapify(int* a, int i, int n)
{
	int j, temp;
	temp = a[i];
	j = 2 * i;
	while (j <= n)
	{
		if (j < n && a[j + 1] > a[j])
			j = j + 1;
		if (temp > a[j])
			break;
		else if (temp <= a[j])
		{
			a[j / 2] = a[j];
			j = 2 * j;
		}
	}
	a[j / 2] = temp;
	return;
}
void build_maxheap(int* a, int n)
{
	int i;
	for (i = n / 2; i >= 1; i--)
	{
		max_heapify(a, i, n);
	}
}

int main()
{
	float n;
	int i, x;
	cout << "Enter no of elements of array\n";
	cin >> n;
	int a[20];
	for (i = 1; i <= n; i++)
	{
		cout << "enter element" << (i) << endl;
		cin >> a[i];
	}
	build_maxheap(a, n);
	cout << "Max Heap\n";
	for (i = 1; i <= n; i++)
	{
		cout << a[i] << endl;
	}
	int flag = 0;
	cout << "\n\nEnter number to search : ";
	cin >> x;
	for (i = 1; i <= n; i++)
	{
		if (x == a[i])
			flag = 1;
	}
	if (flag == 1)
		cout << "Found";
	else
		cout << "Not found";
}
