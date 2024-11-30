# EditMaster_Text_Editor
This program implements a text editor using a **Balanced Binary Search Tree (BST)** and **Stack** data structures.

Each line of text is saved as a **node** in the BST. The node contains:
- **Key (Line Number):** Used to maintain the ordering of the lines.
- **Data (Text):** The actual line of text.
- **Pointers to Left and Right Nodes:** To navigate through the BST.

The program also uses a **Stack data structure** to store operations for implementing the Undo function.

---

## Features:

### 1. **Open an Existing File**
- Parse the text file line by line.
- Insert each line into the BST as a new node, with the line number as the key and the text as the value.

---

### 2. **Save to a File**
- Perform an **in-order traversal** of the BST to retrieve the text in sorted line order.
- Write each line to the file sequentially.

---

### 3. **Insert Text into Line n**
- Given a line number `n` and the text to insert:
  1. Traverse the BST to find where to insert the new line.
  2. Insert the new line as a node in the BST.
  3. **Shift Line Numbers**: Increment the keys of all nodes with line numbers greater than or equal to `n`.

---

### 4. **Delete Line n**
- Traverse the BST to find the node with the key `n`.
- Remove the node from the BST while maintaining its balanced structure.
- **Shift Line Numbers**: Decrement the keys of all nodes with line numbers greater than `n`.

---

### 5. **Move Line n to Line m**
- Retrieve the text at line `n` and delete the node from the BST.
- Insert the text at line `m` by creating a new node with the updated key.
- Adjust other line numbers as necessary to maintain order.

---

### 6. **Replace Text in Line n**
- Traverse the BST to find the node with the key `n`.
- Update the text data of the node.

---

### 7. **Next Page**
- Display the next `k` lines (where `k` is a predefined page size).
- Use an **in-order traversal** to retrieve the next `k` nodes from the current position.

---

### 8. **Previous Page**
- Display the previous `k` lines.
- Use the BST’s in-order traversal and keep track of the previously accessed lines.

---

### 9. **Undo**
- Use a **Stack** to store operations performed (insert, delete, move, or replace).
- To undo an operation:
  - Pop the last operation from the stack.
  - Reverse the effect of the operation in the BST.

---

## Internal Implementation Notes:

### **BST Node Structure**
Each BST node consists of:
- `int key`: The line number (used to maintain order).
- `string text`: The content of the line.
- `Node* left`: Pointer to the left child.
- `Node* right`: Pointer to the right child.

Example:
```cpp
struct Node {
    int key;           // Line number
    string text;       // Text content of the line
    Node* left;        // Left child
    Node* right;       // Right child

    Node(int k, string t) : key(k), text(t), left(nullptr), right(nullptr) {}
};
