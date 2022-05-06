# Trees

[Reading](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-15/resources/Trees.html)

Node - A Tree node is a component which may contain its own values, and references to other nodes
Root - The root is the node at the beginning of the tree
K - A number that specifies the maximum number of children any node may have in a k-ary tree. In a binary tree, k = 2.
Left - A reference to one child node, in a binary tree
Right - A reference to the other child node, in a binary tree
Edge - The edge in a tree is the link between a parent and child node
Leaf - A leaf is a node that does not have any children
Height - The height of a tree is the number of edges from the root to the furthest leaf

Traversal is the way to move through a tree and access what is in the nodes. The two categories of traversals are Depth First and Breadth First.

## Depth First

This is where we prioritize going through the depth, or height, of the tree first. There are many methods, all of which change the order in which you search/print the `root`.

Pre-order: root >> left >> right
In-order: left >> root >> right
Post-order: left >> right >> root

The most common way to traverse through a tree is to use recursion. With these traversals, we rely on the call stack to navigate back up the tree when we have reached the end of a sub-path.

### Pre-order

Pseudocode given for pre-order from reading:
```
Let’s break down the pre-order traversal. Here is the pseudocode for this traversal method:

ALGORITHM preOrder(root)

  OUTPUT <-- root.value

  if root.left is not NULL
      preOrder(root.left)

  if root.right is not NULL
      preOrder(root.right)

```

Pre-order means that the root has to be looked at first. In our case, looking at the root just means that we output its value. When we call preOrder for the first time, the root will be added to the call stack.

This means that we will output the root.value out to the console. Then, our next block of code instructs us to check if our root has a left node set. If the root does, we will then send the left node to our preOrder method recursively. This means that we make another function call, where B is our new root.

This process continues until we reach a leaf node.

It’s important to note a few things that are about to happen:

The program will look for both a root.left and a root.right. Both will return null, so it will end the execution of that method call
D will pop off of the call stack and the root will be reassigned back to B
This is the heart of recursion: when we complete a function call, we pop it off the stack and are able to continue execution through the previous function call

The code block will now pick up where it left off when B was the root. Since it already looked for root.left, it will now look for root.right.

E will output to the console. Since E is a leaf, it will complete the method code block, and pop E off of the call stack and make its way back up to B.

In the function call, B has already checked for root.left, and root.right. There are no further lines of code to execute, so B will be popped off the call stack, so that we can resume execution of A.

Following the same pattern as we did with the other nodes, A’s call stack frame will pick up where it left off, and check out root.right. C will be added to the call stack frame, and it will become the new function’s root.

C will be outputted to the console, and root.left will be evaluated. Because C has a left child, preOrder will be called, with the parameter root.left.

At this point, the program will find that F does not have any children and it will make its way back up the call stack up to C.

C does not have a root.right, so it will pop off the call stack and return to A.

## Pseudo Code for Pre, In, and Post-Order:

Pre-order:

```
ALGORITHM preOrder(root)
// INPUT <-- root node
// OUTPUT <-- pre-order output of tree node's values

    OUTPUT <-- root.value

    if root.left is not Null
        preOrder(root.left)

    if root.right is not NULL
        preOrder(root.right)
```

In-Order:

```
ALGORITHM inOrder(root)
// INPUT <-- root node
// OUTPUT <-- in-order output of tree node's values

    if root.left is not NULL
        inOrder(root.left)

    OUTPUT <-- root.value

    if root.right is not NULL
        inOrder(root.right)
```

Post-Order:

```
ALGORITHM postOrder(root)
// INPUT <-- root node
// OUTPUT <-- post-order output of tree node's values

    if root.left is not NULL
        postOrder(root.left)

    if root.right is not NULL
        postOrder(root.right)

    OUTPUT <-- root.value
```

The biggest difference in the three is when you are looking at the Root node.

## Breadth First

Breadth first traversal iterates through the tree by going through each level of the tree node-by-node.

Traditionally, breadth first traversal uses a queue (instead of the call stack via recursion) to traverse the width/breadth of the tree. Let’s break down the process.

Given our starting tree shown above, let’s start by putting the root into the queue.
Now that we have one node in our queue, we can dequeue it and use that node in our code.
From our dequeued node A, we can enqueue the left and right child (in that order).

This leaves us with B as the new front of our queue. We can then repeat the process we did with A: Dequeue the front node, enqueue that node’s left and right nodes, and move to the next new front of the queue.

Now our front is C, so we repeat the dequeue + enqueue children process.
And we continue onwards. When we reach a node that doesn’t have any children, we just dequeue it without any further enqueue.

Pseudocode for above from reading:

```
ALGORITHM breadthFirst(root)
// INPUT  <-- root node
// OUTPUT <-- front node of queue to console

  Queue breadth <-- new Queue()
  breadth.enqueue(root)

  while ! breadth.is_empty()
    node front = breadth.dequeue()
    OUTPUT <-- front.value

    if front.left is not NULL
      breadth.enqueue(front.left)

    if front.right is not NULL
      breadth.enqueue(front.right)
```

In all of our examples, we’ve been using a Binary Tree. Trees can have any number of children per node, but Binary Trees restrict the number of children to two (hence our left and right children).

## K-ary Trees

If Nodes are able have more than 2 child nodes, we call the tree that contains them a K-ary Tree. In this type of tree we use K to refer to the maximum number of children that each Node is able to have.

```
ALGORITHM breadthFirst(root)
// INPUT  <-- root node
// OUTPUT <-- front node of queue to console

  Queue breadth <-- new Queue()
  breadth.enqueue(root)

  while ! breadth.is_empty()
    node front = breadth.dequeue()
    OUTPUT <-- front.value

    for child in front.children
        breadth.enqueue(child)
```

### Adding a node

Because there are no structural rules for where nodes are “supposed to go” in a binary tree, it really doesn’t matter where a new node gets placed.

One strategy for adding a new node to a binary tree is to fill all “child” spots from the top down. To do so, we would leverage the use of breadth first traversal. During the traversal, we find the first node that does not have all its children filled, and insert the new node as a child. We fill the child slots from left to right.

In the event you would like to have a node placed in a specific location, you need to reference both the new node to create, and the parent node which the child is attached to.

### Big O

The Big O time complexity for inserting a new node is O(n). Searching for a specific node will also be O(n). Because of the lack of organizational structure in a Binary Tree, the worst case for most operations will involve traversing the entire tree. If we assume that a tree has n nodes, then in the worst case we will have to look at n items, hence the O(n) complexity.

The Big O space complexity for a node insertion using breadth first insertion will be O(w), where w is the largest width of the tree. For example, in the above tree, w is 4.

A “perfect” binary tree is one where every non-leaf node has exactly two children. The maximum width for a perfect binary tree, is 2^(h-1), where h is the height of the tree. Height can be calculated as log n, where n is the number of nodes.


### Binary Search Trees

A Binary Search Tree (BST) is a type of tree that does have some structure attached to it. In a BST, nodes are organized in a manner where all values that are smaller than the root are placed to the left, and all values that are larger than the root are placed to the right.

### Searching a BST

Searching a BST can be done quickly, because all you do is compare the node you are searching for against the root of the tree or sub-tree. If the value is smaller, you only traverse the left side. If the value is larger, you only traverse the right side.

Let’s say we are searching 15. We start by comparing the value 15 to the value of the root, 23.

15 < 23, so we traverse the left side of the tree. We then treat 8 as our new “root” to compare against.

15 > 8, so we traverse the right side. 16 is our new root.

15 < 16, so we traverse the left side. And aha! 15 is our new root and also a match with what we were searching for.

The best way to approach a BST search is with a while loop. We cycle through the while loop until we hit a leaf, or until we reach a match with what we’re searching for.



[Back](README.md)