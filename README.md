# codeHere are C programs for each of the tasks you mentioned:

---

### 1. **Matrix Multiplication**

```c
#include <stdio.h>
int main() {
    int a[10][10], b[10][10], c[10][10] = {0};
    int i, j, k, r1, c1, r2, c2;

    printf("Enter rows and columns of first matrix: ");
    scanf("%d%d", &r1, &c1);
    printf("Enter rows and columns of second matrix: ");
    scanf("%d%d", &r2, &c2);

    if (c1 != r2) {
        printf("Matrix multiplication not possible.\n");
        return 0;
    }

    printf("Enter elements of first matrix:\n");
    for (i = 0; i < r1; i++)
        for (j = 0; j < c1; j++)
            scanf("%d", &a[i][j]);

    printf("Enter elements of second matrix:\n");
    for (i = 0; i < r2; i++)
        for (j = 0; j < c2; j++)
            scanf("%d", &b[i][j]);

    for (i = 0; i < r1; i++)
        for (j = 0; j < c2; j++)
            for (k = 0; k < c1; k++)
                c[i][j] += a[i][k] * b[k][j];

    printf("Resultant matrix:\n");
    for (i = 0; i < r1; i++) {
        for (j = 0; j < c2; j++)
            printf("%d ", c[i][j]);
        printf("\n");
    }
    return 0;
}
```

---

### 2. **Odd or Even from a Set**

```c
#include <stdio.h>
int main() {
    int n, i, num;
    printf("Enter how many numbers: ");
    scanf("%d", &n);
    printf("Enter numbers:\n");
    for (i = 0; i < n; i++) {
        scanf("%d", &num);
        if (num % 2 == 0)
            printf("%d is Even\n", num);
        else
            printf("%d is Odd\n", num);
    }
    return 0;
}
```

---

### 3. **Factorial without Recursion**

```c
#include <stdio.h>
int main() {
    int n, i;
    long long fact = 1;
    printf("Enter a number: ");
    scanf("%d", &n);
    for (i = 1; i <= n; i++)
        fact *= i;
    printf("Factorial = %lld\n", fact);
    return 0;
}
```

---

### 4. **Fibonacci without Recursion**

```c
#include <stdio.h>
int main() {
    int n, a = 0, b = 1, c, i;
    printf("Enter number of terms: ");
    scanf("%d", &n);
    printf("Fibonacci Series: %d %d ", a, b);
    for (i = 2; i < n; i++) {
        c = a + b;
        printf("%d ", c);
        a = b;
        b = c;
    }
    return 0;
}
```

---

### 5. **Factorial using Recursion**

```c
#include <stdio.h>
long long factorial(int n) {
    if (n == 0 || n == 1)
        return 1;
    return n * factorial(n - 1);
}
int main() {
    int n;
    printf("Enter a number: ");
    scanf("%d", &n);
    printf("Factorial = %lld\n", factorial(n));
    return 0;
}
```

---

### 6. **Fibonacci using Recursion**

```c
#include <stdio.h>
int fibonacci(int n) {
    if (n == 0)
        return 0;
    if (n == 1)
        return 1;
    return fibonacci(n - 1) + fibonacci(n - 2);
}
int main() {
    int n, i;
    printf("Enter number of terms: ");
    scanf("%d", &n);
    printf("Fibonacci Series: ");
    for (i = 0; i < n; i++)
        printf("%d ", fibonacci(i));
    return 0;
}
```

---

### 7. **Array Operations (Insert, Delete, Display)**

```c
#include <stdio.h>
int main() {
    int a[100], n = 0, i, choice, pos, val;
    do {
        printf("\n1.Insert 2.Delete 3.Display 4.Exit\n");
        scanf("%d", &choice);
        switch (choice) {
            case 1:
                printf("Enter position and value: ");
                scanf("%d%d", &pos, &val);
                for (i = n; i > pos; i--)
                    a[i] = a[i - 1];
                a[pos] = val;
                n++;
                break;
            case 2:
                printf("Enter position to delete: ");
                scanf("%d", &pos);
                for (i = pos; i < n - 1; i++)
                    a[i] = a[i + 1];
                n--;
                break;
            case 3:
                printf("Array: ");
                for (i = 0; i < n; i++)
                    printf("%d ", a[i]);
                break;
        }
    } while (choice != 4);
    return 0;
}
```

---

### 8. **Linear Search**

```c
#include <stdio.h>
int main() {
    int a[100], n, i, key, found = 0;
    printf("Enter number of elements: ");
    scanf("%d", &n);
    printf("Enter elements:\n");
    for (i = 0; i < n; i++)
        scanf("%d", &a[i]);
    printf("Enter key to search: ");
    scanf("%d", &key);
    for (i = 0; i < n; i++) {
        if (a[i] == key) {
            found = 1;
            break;
        }
    }
    if (found)
        printf("Found at position %d\n", i);
    else
        printf("Not Found\n");
    return 0;
}
```

---

### 9. **Binary Search**

```c
#include <stdio.h>
int main() {
    int a[100], n, i, key, low, high, mid;
    printf("Enter number of elements: ");
    scanf("%d", &n);
    printf("Enter sorted elements:\n");
    for (i = 0; i < n; i++)
        scanf("%d", &a[i]);
    printf("Enter key to search: ");
    scanf("%d", &key);
    low = 0, high = n - 1;
    while (low <= high) {
        mid = (low + high) / 2;
        if (a[mid] == key) {
            printf("Found at position %d\n", mid);
            return 0;
        } else if (a[mid] < key)
            low = mid + 1;
        else
            high = mid - 1;
    }
    printf("Not Found\n");
    return 0;
}
```

---

### 10. **Linked List Operations**

```c
#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node* next;
};

void display(struct Node* head) {
    while (head != NULL) {
        printf("%d -> ", head->data);
        head = head->next;
    }
    printf("NULL\n");
}

void insert(struct Node** head, int val) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = val;
    newNode->next = *head;
    *head = newNode;
}

void delete(struct Node** head, int key) {
    struct Node *temp = *head, *prev = NULL;
    if (temp != NULL && temp->data == key) {
        *head = temp->next;
        free(temp);
        return;
    }
    while (temp != NULL && temp->data != key) {
        prev = temp;
        temp = temp->next;
    }
    if (temp == NULL) return;
    prev->next = temp->next;
    free(temp);
}

int main() {
    struct Node* head = NULL;
    insert(&head, 10);
    insert(&head, 20);
    insert(&head, 30);
    display(head);
    delete(&head, 20);
    display(head);
    return 0;
}
```

---

### 11. **Stack Operations: PUSH, POP, PEEK**

```c
#include <stdio.h>
#define SIZE 100
int stack[SIZE], top = -1;

void push(int val) {
    if (top == SIZE - 1)
        printf("Stack Overflow\n");
    else
        stack[++top] = val;
}

void pop() {
    if (top == -1)
        printf("Stack Underflow\n");
    else
        printf("Popped: %d\n", stack[top--]);
}

void peek() {
    if (top == -1)
        printf("Stack is Empty\n");
    else
        printf("Top: %d\n", stack[top]);
}

int main() {
    push(10); push(20); peek(); pop(); peek();
    return 0;
}
```

---

### 12. **Application of Stack (Notations - Infix to Postfix)**

```c
#include <stdio.h>
#include <ctype.h>
#define SIZE 100
char stack[SIZE];
int top = -1;

void push(char c) {
    stack[++top] = c;
}
char pop() {
    return stack[top--];
}
int precedence(char c) {
    if (c == '^') return 3;
    if (c == '*' || c == '/') return 2;
    if (c == '+' || c == '-') return 1;
    return 0;
}
void infixToPostfix(char* expr) {
    int i = 0;
    while (expr[i]) {
        char c = expr[i];
        if (isalnum(c))
            printf("%c", c);
        else if (c == '(')
            push(c);
        else if (c == ')') {
            while (stack[top] != '(')
                printf("%c", pop());
            pop(); // Remove '('
        } else {
            while (top != -1 && precedence(stack[top]) >= precedence(c))
                printf("%c", pop());
            push(c);
        }
        i++;
    }
    while (top != -1)
        printf("%c", pop());
}

int main() {
    char expr[] = "a+b*(c^d-e)^(f+g*h)-i";
    printf("Postfix: ");
    infixToPostfix(expr);
    return 0;
}
```

---

### 13. **Queue Operations**

```c
#include <stdio.h>
#define SIZE 100
int queue[SIZE], front = -1, rear = -1;

void enqueue(int val) {
    if (rear == SIZE - 1)
        printf("Queue Overflow\n");
    else {
        if (front == -1) front = 0;
        queue[++rear] = val;
    }
}
void dequeue() {
    if (front == -1 || front > rear)
        printf("Queue Underflow\n");
    else
        printf("Dequeued: %d\n", queue[front++]);
}
void display() {
    if (front == -1)
        printf("Queue is Empty\n");
    else {
        printf("Queue: ");
        for (int i = front; i <= rear; i++)
            printf("%d ", queue[i]);
        printf("\n");
    }
}
int main() {
    enqueue(10); enqueue(20); display(); dequeue(); display();
    return 0;
}
```

---

### 14. **Tree Traversals (Inorder, Preorder, Postorder)**

```c
#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node *left, *right;
};

struct Node* newNode(int data) {
    struct Node* node = (struct Node*)malloc(sizeof(struct Node));
    node->data = data;
    node->left = node->right = NULL;
    return node;
}

void inorder(struct Node* root) {
    if (root) {
        inorder(root->left);
        printf("%d ", root->data);
        inorder(root->right);
    }
}
void preorder(struct Node* root) {
    if (root) {
        printf("%d ", root->data);
        preorder(root->left);
        preorder(root->right);
    }
}
void postorder(struct Node* root) {
    if (root) {
        postorder(root->left);
        postorder(root->right);
        printf("%d ", root->data);
    }
}

int main() {
    struct Node* root = newNode(1);
    root->left = newNode(2);
    root->right = newNode(3);
    root->left->left = newNode(4);
    root->left->right = newNode(5);

    printf("Inorder: ");
    inorder(root);
    printf("\nPreorder: ");
    preorder(root);
    printf("\nPostorder: ");
    postorder(root);

    return 0;
}
```

---

Let me know if you want all these bundled into a PDF or individual files.
