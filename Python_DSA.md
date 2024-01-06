# Python DSA

# Important Things to Remember

---

- Python uses dynamic arrays → if an operation like `list.insert(element)` causes the array to automatically resize, it will **increase the time complexity to O(n)** because **all elements have to be linearly copied over**

# Python Primitive Data Type Common Sizes

---

1. **int**: Typically 4 bytes (32-bit) or 8 bytes (64-bit).
2. **float**: Usually 8 bytes.
3. **bool**: About 1 byte.
4. **NoneType**: Around 16 bytes.
5. **str**: Variable, depending on content and encoding. In Python 3, strings are **Unicode by default**, and each character can take up to 4 bytes.
6. **bytes**: Variable, based on length.
7. **bytearray**: Variable, based on length.
8. **list**: Variable, grows dynamically.
9. **tuple**: Generally smaller than lists.
10. **set**: Variable, depends on elements.
11. **dict**: Variable, depends on key-value pairs.

These sizes can vary based on Python version and platform. Use **`sys.getsizeof()`** for more accurate measurements.

# **Big O Notation**

---

**Big O notation** is used to analyze the **time complexity** and **space complexity** of algorithms and data structures. It provides a way to describe how the performance of an algorithm or data structure scales as the input size grows.

Big O notation looks at **worst case analysis**

### **Time Complexity**

- **Time complexity** measures the **amount of time an algorithm takes to run** as a function of the input size. It helps us understand how the algorithm's execution time increases with larger inputs.
- Common time complexities:
    - O(1) - Constant time: The algorithm's runtime is constant, regardless of the input size.
    - O(log n) - Logarithmic time: The runtime grows slowly as the input size increases.
    - O(n) - Linear time: The runtime grows linearly with the input size.
    - O(n log n) - Linearithmic time: Slightly worse than linear time.
    - O(n^2) - Quadratic time: The runtime grows with the square of the input size.
    - O(2^n) - Exponential time: The runtime grows exponentially with the input size.
- To calculate time complexity, count the number of basic operations (e.g., comparisons, assignments) in terms of the input size and express it as a function of **n**, the size of the input.

### **Space Complexity**

- **Space complexity** measures the **amount of memory an algorithm or data structure uses** as a function of the input size. It helps us understand how memory usage increases with larger inputs.
- Common space complexities:
    - O(1) - Constant space: The algorithm uses a fixed amount of memory.
    - O(n) - Linear space: The memory usage grows linearly with the input size.
    - O(n^2) - Quadratic space: The memory usage grows with the square of the input size.
- To calculate space complexity, consider the memory used by data structures, variables, and recursive calls, and express it as a function of **n**.

### Code **Example**

**Calculating Time and Space Complexity**:

```python
def find_max(arr):
    max_val = arr[0]  # O(1) space
    for num in arr:  # O(n) time
        if num > max_val:  # O(1) time
            max_val = num  # O(1) space
    return max_val  # O(1) space

# Time Complexity: O(n)
# Space Complexity: O(1)
```

# **Arrays in Python**

---

- **Arrays** in Python are implemented as **lists**.
- Lists in Python are dynamic arrays that can grow or shrink in size.

### **Time Complexity:**

1. **Access**: Accessing an element by index is O(1) since Python uses **zero-based indexing**.
2. **Insertion**:
    - **Append**: Adding an element to the end of the list is typically O(1) on average but may occasionally be O(n) if the list needs to be resized.
    - **Insert**: Inserting an element at a specific index is O(n) because it may require shifting elements to make space.
3. **Deletion**:
    - **Remove**: Removing an element by value is O(n) since it may need to search for the value in the list.
    - **Pop**: Removing an element by index is O(n) because it requires shifting elements after the removed one.
4. **Search**:
    - **Linear Search**: Searching for an element in an unsorted list is O(n) as it may need to examine all elements.
    - **Binary Search**: Searching in a sorted list is O(log n), but the list must be sorted first.

### **Memory Management:**

- Lists in Python are implemented as dynamic arrays, which means they can grow or shrink as needed.
- When a list outgrows its current memory allocation, Python allocates a larger block of memory, typically doubling the previous size.
- Python may also over-allocate memory to avoid frequent re-allocations.
- The **`sys.getsizeof()`** function can be used to estimate the memory usage of a list.

### **Memory Address:**

- You can use the **`id()`** function to obtain the memory address of a list or any object.
- Example:
    
    ```python
    my_list = [1, 2, 3]
    address = id(my_list)
    print(f"Memory address: {address}")
    ```
    

# **Linked Lists in Python**

---

**Node Class:**

```python
class Node:
    def __init__(self, value):
        self.value = value
        self.next = None
```

### **Time Complexity:**

- **Access**: O(n) - Linked lists require linear time to access elements as you may need to traverse from the beginning to the desired node.
- **Insertion**:
    - **Insert at Head**: O(1) - You can insert a node at the head of the list in constant time.
    - **Insert at Tail**: O(n) - To insert at the end, you'll need to traverse the entire list.
    - **Insert at Specific Position**: O(n) - If you know the position, you'll need to traverse to that position.
- **Deletion**:
    - **Delete at Head**: O(1) - Removing the head node is a constant-time operation.
    - **Delete at Tail**: O(n) - To delete the last node, you'll need to traverse the list.
    - **Delete at Specific Position**: O(n) - If you know the position, you'll need to traverse to that position.

### **Memory Management:**

- Linked lists dynamically allocate memory for each node, which allows them to grow or shrink efficiently.
- Each node consists of the value and a reference to the next node. The size of a node depends on the value's size and the reference size.

### **When to Use Linked Lists:**

- Use linked lists when you need efficient insertions and deletions at the beginning of the list (head) because these operations are O(1).
- Linked lists are useful in scenarios where the list size is not known in advance, as they can grow or shrink without excessive memory allocation.
- However, for random access and when the size is fixed or known, arrays or other data structures may be more suitable.
- **Code Examples**
    
    **Insertion at the Head:**
    
    ```python
    class LinkedList:
        def __init__(self):
            self.head = None
    
        def insert_at_head(self, value):
            new_node = Node(value)
            new_node.next = self.head
            self.head = new_node
    ```
    
    **Insertion at the Tail:**
    
    ```python
    class LinkedList:
        def __init__(self):
            self.head = None
    
        def insert_at_tail(self, value):
            new_node = Node(value)
            if not self.head:
                self.head = new_node
                return
            current = self.head
            while current.next:
                current = current.next
            current.next = new_node
    ```
    
    **Search for a Value:**
    
    ```python
    class LinkedList:
        def __init__(self):
            self.head = None
    
        def search(self, value):
            current = self.head
            while current:
                if current.value == value:
                    return True
                current = current.next
            return False
    ```
    
    **Deletion by Value:**
    
    ```python
    class LinkedList:
        def __init__(self):
            self.head = None
    
        def delete(self, value):
            if not self.head:
                return
    
            if self.head.value == value:
                self.head = self.head.next
                return
    
            current = self.head
            while current.next:
                if current.next.value == value:
                    current.next = current.next.next
                    return
                current = current.next
    ```
    
    **Traversal and Printing:**
    
    ```python
    class LinkedList:
        def __init__(self):
            self.head = None
    
        def print_list(self):
            current = self.head
            while current:
                print(current.value, end=" -> ")
                current = current.next
            print("None")
    ```
    
    You can create a linked list instance and use these functions to manipulate and work with the linked list data structure. For example:
    
    ```python
    my_linked_list = LinkedList()
    my_linked_list.insert_at_head(10)
    my_linked_list.insert_at_head(20)
    my_linked_list.insert_at_tail(30)
    my_linked_list.print_list()  # Output: 20 -> 10 -> 30 -> None
    my_linked_list.delete(10)
    my_linked_list.print_list()  # Output: 20 -> 30 -> None
    print(my_linked_list.search(20))  # Output: True
    ```
    

# Hash Table/Map (Python Dictionary {})

---

A hash table, also known as a hash map, is a data structure that stores **key-value pairs (AKA Python Dictionary {}).** It provides **efficient data retrieval** by using a hash function to map keys to specific locations in memory, making it a popular choice for quick lookups.

### **Basic Operations:**

1. **Insertion (Add a Key-Value Pair):**
    - Time Complexity: O(1) on average (can be O(n) in rare cases → For example, if the solution to hash collisions was to insert a linked list at the given memory location, you have to traverse the list)
    
    ```python
    my_dict = {}
    my_dict["key1"] = "value1"
    my_dict["key2"] = "value2"
    ```
    
2. **Access (Retrieve a Value by Key):**
    - Time Complexity: O(1) on average (can be O(n) in rare cases → For example, if the solution to hash collisions was to insert a linked list at the given memory location, you have to traverse the list)
    
    ```python
    value = my_dict["key1"]
    ```
    
3. **Deletion (Remove a Key-Value Pair):**
    - Time Complexity: O(1) on average (can be O(n) in rare cases → For example, if the solution to hash collisions was to insert a linked list at the given memory location, you have to traverse the list)
    
    ```python
    del my_dict["key1"]
    ```
    

### **Memory Management:**

- Hash tables manage memory dynamically, resizing as needed to accommodate a growing number of entries. This ensures efficient memory usage.

### **When to Use a Hash Table:**

- Use hash tables when you need fast access to data based on unique keys. Common use cases include:
    - Storing and retrieving data with key-value relationships.
    - Implementing caches for efficient data retrieval.
    - Counting occurrences of elements (e.g., frequency of words in a text).

### Code **Example:**

```python
# Creating a hash map
my_dict = {}
my_dict["Alice"] = 25
my_dict["Bob"] = 30
my_dict["Charlie"] = 28

# Accessing values
print(my_dict["Alice"])  # Output: 25

# Removing a key-value pair
del my_dict["Bob"]
```

### **Hash Collision Solutions**

1. **Chaining (Open Hashing):**
    - Store colliding key-value pairs in linked lists at the same hash index.
    - **Time Complexity**:
        - Insertion: O(1) on average, O(n) in the worst case (if all keys collide).
        - Retrieval: O(1) on average, O(n) in the worst case (if all keys collide).
        - Deletion: O(1) on average, O(n) in the worst case (if all keys collide).
2. **Open Addressing (Closed Hashing):**
    - Store colliding key-value pairs directly in the array with probing for the next available slot.
    - **Time Complexity**:
        - Insertion: O(1) on average, O(n) in the worst case (if table is nearly full).
        - Retrieval: O(1) on average, O(n) in the worst case (if table is nearly full).
        - Deletion: O(1) on average, O(n) in the worst case (if table is nearly full).
3. **Double Hashing (Open Addressing):**
    - Use a secondary hash function to calculate the step size for probing.
    - **Time Complexity**:
        - Insertion: O(1) on average, O(n) in the worst case (if table is nearly full).
        - Retrieval: O(1) on average, O(n) in the worst case (if table is nearly full).
        - Deletion: O(1) on average, O(n) in the worst case (if table is nearly full).
4. **Quadratic Probing (Open Addressing):**
    - Use a quadratic sequence to probe for the next available slot.
    - **Time Complexity**:
        - Insertion: O(1) on average, O(n) in the worst case (if table is nearly full).
        - Retrieval: O(1) on average, O(n) in the worst case (if table is nearly full).
        - Deletion: O(1) on average, O(n) in the worst case (if table is nearly full).
5. **Cuckoo Hashing:**
    - Use multiple hash functions and two hash tables, migrating keys if collisions occur.
    - **Time Complexity**:
        - Insertion: O(1) on average, O(n) in the worst case (if migration is frequent).
        - Retrieval: O(1) on average, O(n) in the worst case (if migration is frequent).
        - Deletion: O(1) on average, O(n) in the worst case (if migration is frequent).
        

# Stack (LIFO)

---

A stack is a linear data structure that follows the Last-In-First-Out (LIFO) principle. It is used to manage elements with two main operations: "push" to add an item to the top of the stack and "pop" to remove the top item.

### **Basic Operations:**

- **`push(item)`**: Adds an item to the top of the stack.
- **`pop()`**: Removes and returns the top item from the stack.
- **`peek()`**: Returns the top item without removing it.
- **`isEmpty()`**: Checks if the stack is empty.
- **`size()`**: Returns the number of elements in the stack.

### **Time Complexity:**

- **`push(item)`**: O(1)
- **`pop()`**: O(1)
- **`peek()`**: O(1)
- **`isEmpty()`**: O(1)
- **`size()`**: O(1)

### **Memory Management:**

- Stacks in Python can be implemented using lists.
- Lists automatically manage memory allocation, so you don't need to worry about memory management when using Python lists as stacks.

### **When to Use a Stack:**

- Stacks are suitable for scenarios where elements need to be accessed and removed in a last-in-first-out order.
- Use cases include implementing function call stacks, evaluating expressions, and managing undo/redo functionality in applications.

### Code **Example:**

```python
# Creating an empty stack
stack = []

# Pushing elements onto the stack
stack.append(1)
stack.append(2)
stack.append(3)

# Popping elements from the stack
top_element = stack.pop()  # Removes and returns 3
```

**Note:** In Python, you can also use the **`collections.deque`** class as a double-ended queue (deque) to implement a stack efficiently. Deques provide O(1) time complexity for **`append()`** and **`pop()`** operations from both ends, making them suitable for stack operations.

# Queue (FIFO)

---

"enqueue" to add an item to the back of the queue and "dequeue" to remove and return the front item.

### **Basic Operations:**

- **`enqueue(item)`**: Adds an item to the back of the queue.
- **`dequeue()`**: Removes and returns the front item from the queue.
- **`peek()`**: Returns the front item without removing it.
- **`isEmpty()`**: Checks if the queue is empty.
- **`size()`**: Returns the number of elements in the queue.

### **Time Complexity:**

- **`enqueue(item)`**: O(1)
- **`dequeue()`**: O(1)
- **`peek()`**: O(1)
- **`isEmpty()`**: O(1)
- **`size()`**: O(1)

### **Memory Management:**

- Queues in Python can be implemented using lists.
- Lists automatically manage memory allocation, so you don't need to worry about memory management when using Python lists as queues.

### **When to Use a Queue:**

- Queues are suitable for scenarios where elements need to be processed in a first-in-first-out order.
- Use cases include task scheduling, managing requests in web applications, and breadth-first search algorithms.

### Code **Example:**

```python
# Creating an empty queue
queue = []

# Enqueuing elements
queue.append(1)
queue.append(2)
queue.append(3)

# Dequeuing elements
front_element = queue.pop(0)  # Removes and returns 1
```

# Binary Search Tree

---

A Binary Search Tree (BST) is a hierarchical data structure where **each node has at most two child nodes**, referred to as the left child and the right child. 

The root node is the topmost node in the tree. In a BST, all nodes in the left subtree have values less than the root node, and all nodes in the right subtree have values greater than the root node. This property makes BSTs **efficient for search operations.**

**A tree is a special kind of graph**

### **Time Complexity:**

- **Insertion:** O(log n) on average (O(n) in the worst case when the tree is unbalanced).
- **Deletion:** O(log n) on average (O(n) in the worst case when the tree is unbalanced).
- **Search:** O(log n) on average (O(n) in the worst case when the tree is unbalanced).

### **Memory Management:**

BSTs are typically implemented using nodes, where each node contains data and references to its left and right children. In Python, you can create a BST using classes and references.

### **Tree Traversals:**

1. **Inorder Traversal:** Visit left subtree, then the root, then the right subtree.
    
    Root is in between left and right subtree
    
    ```python
    def inorder_traversal(node):
        if node:
            inorder_traversal(node.left)
            print(node.data)
            inorder_traversal(node.right)
    ```
    
2. **Preorder Traversal:** Visit the root, then the left subtree, then the right subtree.
    
    Root comes before left and right subtree
    
    ```python
    def preorder_traversal(node):
        if node:
            print(node.data)
            preorder_traversal(node.left)
            preorder_traversal(node.right)
    ```
    
3. **Postorder Traversal:** Visit the left subtree, then the right subtree, then the root.
    
    Root comes after left and right subtree
    
    ```python
    def postorder_traversal(node):
        if node:
            postorder_traversal(node.left)
            postorder_traversal(node.right)
            print(node.data)
    ```
    

### **When to Use a BST:**

- Use a BST when you need efficient search, insertion, and deletion of elements in sorted order.
- BSTs are suitable for scenarios where the data needs to be stored in a sorted order and you want to maintain that order efficiently.

Remember that the efficiency of a BST depends on its balance. If the tree becomes unbalanced (e.g., degenerates into a linked list), the time complexity for operations can degrade to O(n). To maintain balance, you can consider using self-balancing binary search trees like AVL trees or Red-Black trees in certain situations.

### Code Examples

```python
class TreeNode:
    def __init__(self, key):
        self.left = None
        self.right = None
        self.val = key

def insert(root, key):
    if root is None:
        return TreeNode(key)
    else:
        if key < root.val:
            root.left = insert(root.left, key)
        else:
            root.right = insert(root.right, key)
    return root

def search(root, key):
    if root is None or root.val == key:
        return root

    if key < root.val:
        return search(root.left, key)

    return search(root.right, key)

def find_min_node(node):
    current = node
    while current.left is not None:
        current = current.left
    return current

def delete(root, key):
    if root is None:
        return root

    if key < root.val:
        root.left = delete(root.left, key)
    elif key > root.val:
        root.right = delete(root.right, key)
    else:
        if root.left is None:
            return root.right
        elif root.right is None:
            return root.left

        # Node with two children: get the inorder successor (smallest in the right subtree)
        root.val = find_min_node(root.right).val
        root.right = delete(root.right, root.val)

    return root

# Example usage:
root = None
root = insert(root, 50)
insert(root, 30)
insert(root, 20)
insert(root, 40)
insert(root, 70)
insert(root, 60)
insert(root, 80)

print("Original BST:")
print("       50")
print("      /  \\")
print("     30   70")
print("    / \\   / \\")
print("   20  40 60  80")

# Deleting a node (e.g., deleting 30)
root = delete(root, 30)

print("\nBST after deleting 30:")
print("       50")
print("      /  \\")
print("     40   70")
print("    /     / \\")
print("   20    60  80")
```

# **Graph**

---

types of graphs: directed/undirected, weighted/unweighted, cyclic/acyclic. In Python, graphs can be represented using dictionaries or custom classes.

### **Time Complexity:**

- The time complexity for traversing a graph using algorithms like B**readth-First Search (BFS) or Depth-First Search (DFS) is O(V + E), where V is the number of vertices (nodes) and E is the number of edges.**
- Insertion, removal, or searching for specific nodes or edges in a graph typically depends on the chosen data structure for implementation.

### **Memory Management:**

- Graphs in Python can be represented using dictionaries, where nodes are keys, and their corresponding edges are stored as values in lists or sets. Memory usage depends on the chosen representation.

### **Types of Graphs:**

1. **Undirected Unweighted Graph:**

```python
# Using a dictionary to represent an undirected unweighted graph
graph = {
    'A': ['B', 'C'],
    'B': ['A', 'D', 'E'],
    'C': ['A', 'F'],
    'D': ['B'],
    'E': ['B', 'F'],
    'F': ['C', 'E']
}
```

1. **Directed Weighted Graph:**

```python
# Using a dictionary to represent a directed weighted graph
graph = {
    'A': {'B': 2, 'C': 1},
    'B': {'D': 3, 'E': 2},
    'C': {'F': 1},
    'D': {},
    'E': {'F': 2},
    'F': {}
}
```

### **Graph Traversals:**

1. **Breadth-First Search (BFS):** Explore a graph level by level.

```python
from collections import deque

def bfs(graph, start):
    visited = set()
    queue = deque([start])
    while queue:
        node = queue.popleft()
        if node not in visited:
            print(node)
            visited.add(node)
            queue.extend(neighbor for neighbor in graph[node] if neighbor not in visited)

# Example usage
bfs(graph, 'A')
```

1. **Depth-First Search (DFS):** Explore a graph deeper before backtracking.

```python
def dfs(graph, node, visited=None):
    if visited is None:
        visited = set()
    if node not in visited:
        print(node)
        visited.add(node)
        for neighbor in graph[node]:
            dfs(graph, neighbor, visited)

# Example usage
dfs(graph, 'A')
```

### **When to Use a Graph:**

- Use a graph when you need to represent and analyze relationships between elements.
- Graphs are suitable for solving problems involving connectivity, paths, networks, and dependencies.
- Choose the type of graph (directed, undirected, weighted, unweighted) based on your specific problem requirements.

# **Binary Search Algorithm O(log n)**

---

**Dataset must be SORTED**

Binary search is an efficient search algorithm used to find a specific target value within a **sorted** collection of elements. It works by repeatedly dividing the search interval in half until the target element is found or the interval becomes empty.

### **Time Complexity:**

- Binary search has a time complexity of O(log n), where n is the number of elements in the sorted collection.
- This algorithm excels in scenarios with large datasets and is significantly faster than linear search (O(n)) for sorted data.

### **Memory Management:**

- Binary search does not require additional memory proportional to the size of the input data. It operates within the given array or collection.

### **Algorithm Steps (Iterative):**

```python
def binary_search_iterative(arr, target):
    left, right = 0, len(arr) - 1
    while left <= right:
        mid = (left + right) // 2
        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
    return -1
```

### **Algorithm Steps (Recursive):**

```python
# CHECKS BOUNDS !!!!
def binary_search_recursive(arr, target, left, right):
    if left > right:
        return -1
    mid = (left + right) // 2 # // is integer division in Python
    if arr[mid] == target:
        return mid
    elif arr[mid] < target:
        return binary_search_recursive(arr, target, mid + 1, right)
    else:
        return binary_search_recursive(arr, target, left, mid - 1)
```

### **When to Use Binary Search:**

- Use binary search when you have a sorted collection (array, list) and need to quickly locate a specific element.

# **Bubble Sort Algorithm (Educational) O(n^2)**

---

Bubble Sort is a simple sorting algorithm that repeatedly steps through the list, compares adjacent elements, and swaps them if they are in the wrong order. This process continues until the entire list is sorted.

### **Time Complexity:**

- Bubble Sort has a time complexity of **O(n^2)** in the worst-case scenario, where n is the number of elements in the list.
- It is not recommended for large datasets due to its inefficiency compared to more advanced sorting algorithms like Quick Sort or Merge Sort.

### **Memory Management:**

- Bubble Sort operates directly on the given list and does not require additional memory space proportional to the size of the input.

### **Algorithm (Iterative):**

```python
def bubble_sort(arr):
    n = len(arr)
    for i in range(n):
        # Last i elements are already in place, so no need to check them
        for j in range(0, n - i - 1):
            if arr[j] > arr[j + 1]:
                # Swap if the element found is greater than the next element
                arr[j], arr[j + 1] = arr[j + 1], arr[j]
```

### **When to Use Bubble Sort:**

- Bubble Sort is a simple sorting algorithm suitable for **educational purposes and small datasets.**
- It is rarely used in practice for large or real-world applications due to its poor time complexity.
- Consider using Bubble Sort only for educational purposes or when dealing with very small datasets where its simplicity is an advantage.

# **Quicksort**

---

Quicksort is a widely used sorting algorithm known for its efficiency and speed. It follows the divide-and-conquer strategy to sort an array or list. Here are key details about quicksort:

### **Algorithm Steps:**

1. **Pivot Selection:** Choose a pivot element from the array.
2. **Partitioning:** Rearrange the array elements into two sub-arrays. **Elements less than the pivot are placed on the left, and elements greater than the pivot are placed on the right.**
3. **Recursion:** Recursively apply the above two steps to the left and right sub-arrays.
4. **Combine:** Combine the sorted sub-arrays to get the final sorted array.

### **Time Complexity:**

- **Average Case:** O(n log n)
- **Worst Case:** O(n^2) - This occurs when the pivot selection consistently results in unbalanced partitions.
- **Best Case:** O(n log n) - Achieved when the pivot selection consistently results in balanced partitions.

### **Memory Management:**

Quicksort is an in-place sorting algorithm, meaning it doesn't require additional memory allocation for temporary arrays. It sorts the array in its place, which makes it memory-efficient.

### **Recursion vs. Iteration:**

Quicksort is typically implemented using recursion. While it's possible to use an iterative approach with a stack, the recursive version is more common and elegant.

### **When to Use Quicksort:**

- Use quicksort when you need a fast, in-place sorting algorithm.
- It's efficient for sorting large datasets and is often used as a standard sorting algorithm.
- Quicksort is preferred over other sorting algorithms like bubble sort and insertion sort for its average and best-case time complexity.

### **Code Example:**

```python
def quicksort(arr):
    if len(arr) <= 1:
        return arr

    pivot = arr[len(arr) // 2]
    left = [x for x in arr if x < pivot]
    middle = [x for x in arr if x == pivot]
    right = [x for x in arr if x > pivot]

    return quicksort(left) + middle + quicksort(right)

# Example usage:
arr = [3, 6, 8, 10, 1, 2, 1]
sorted_arr = quicksort(arr)
print(sorted_arr)  # Output: [1, 1, 2, 3, 6, 8, 10]
```

# **Insertion Sort**

---

Insertion Sort is a simple sorting algorithm that builds the final sorted array one item at a time. It's an in-place and stable sorting algorithm. Here are key details about insertion sort:

### **Algorithm Steps:**

1. **Initialization:** Start with the second element (assuming the first element is already sorted).
2. **Comparison:** Compare the current element with the elements to its left.
3. **Insertion:** Insert the current element into its correct position among the sorted elements to the left.
4. **Repeat:** Continue this process for each element in the array until the entire array is sorted.

### **Time Complexity:**

- **Average Case:** O(n^2)
- **Worst Case:** O(n^2) - Occurs when the array is sorted in reverse order.
- **Best Case:** O(n) - Occurs when the array is already sorted.

### **Memory Management:**

Insertion Sort is an in-place sorting algorithm, meaning it sorts the array in its place, without requiring additional memory allocation for temporary arrays.

### **Recursion vs. Iteration:**

Insertion Sort is typically implemented using iteration (loops). While recursion is possible, it's not commonly used for this algorithm.

### **When to Use Insertion Sort:**

- Use Insertion Sort when dealing with small datasets or nearly sorted data.
- It's simple to implement and works well when the data is already partially sorted.
- For larger datasets, consider more efficient sorting algorithms like quicksort, merge sort, or heap sort.

### **Code Example:**

```python
def insertion_sort(arr):
    for i in range(1, len(arr)):
        key = arr[i]
        j = i - 1
        while j >= 0 and key < arr[j]:
            arr[j + 1] = arr[j]
            j -= 1
        arr[j + 1] = key

# Example usage:
arr = [12, 11, 13, 5, 6]
insertion_sort(arr)
print(arr)  # Output: [5, 6, 11, 12, 13]
```

# **Merge Sort**

---

Merge Sort is a widely used, efficient, and stable sorting algorithm that follows the divide-and-conquer approach. 

The Python sorting algorithm uses merge sort

### **Algorithm Steps:**

1. **Divide:** Divide the unsorted list into n sublists, each containing one element.
2. **Conquer:** Repeatedly merge sublists to produce new sorted sublists until there is only one sublist remaining.
3. **Merge:** Merge two sublists back into a single sorted sublist by comparing elements from both sublists, ensuring the order is preserved.
4. **Repeat:** Continue this process until all sublists are merged into a single sorted list.

### **Time Complexity:**

- **Average Case:** O(n log n)
- **Worst Case:** O(n log n)
- **Best Case:** O(n log n)

### Space Complexity & **Memory Management:**

- **Space Complexity:** O(n)

Merge Sort is an out-of-place sorting algorithm. **It requires additional memory space to store temporary sublists during the merge phase, making it less memory-efficient than some in-place sorting algorithms.**

### **Recursion vs. Iteration:**

Merge Sort is typically implemented using recursion due to its divide-and-conquer nature. While iteration is possible, recursion is a more natural choice.

### **When to Use Merge Sort:**

- Use Merge Sort when you need a stable and efficient sorting algorithm.
- It's particularly useful for sorting large datasets, as it has a consistent time complexity regardless of the initial order of the data.
- Merge Sort is a good choice when memory usage is not a critical concern.

### **Code Example:**

```python
def merge_sort(arr):
    if len(arr) > 1:
        mid = len(arr) // 2
        left_half = arr[:mid]
        right_half = arr[mid:]

        merge_sort(left_half)
        merge_sort(right_half)

        i = j = k = 0

        while i < len(left_half) and j < len(right_half):
            if left_half[i] < right_half[j]:
                arr[k] = left_half[i]
                i += 1
            else:
                arr[k] = right_half[j]
                j += 1
            k += 1

        while i < len(left_half):
            arr[k] = left_half[i]
            i += 1
            k += 1

        while j < len(right_half):
            arr[k] = right_half[j]
            j += 1
            k += 1

# Example usage:
arr = [12, 11, 13, 5, 6, 7]
merge_sort(arr)
print(arr)  # Output: [5, 6, 7, 11, 12, 13]
```
