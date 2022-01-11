# 401 Reading 10: Stacks and Queues

## Stacks and Queues
[Reading](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-10/resources/stacks_and_queues.html)

A stack is a data structure. It consists of Nodes. Each Node references the next Node in the stack but does not reference the previous Node.

Common termionology, taken from reading:
1. Push - Nodes or items that are put into the stack are pushed

2. Pop - Nodes or items that are removed from the stack are popped. When you attempt to pop an empty stack an exception will be raised.

3. Top - This is the top of the stack.

4. Peek - When you peek you will view the value of the top Node in the stack. When you attempt to peek an empty stack an exception will be raised.

5. IsEmpty - returns true when stack is empty otherwise returns false.

Stacks follow the following concepts:

FILO or First In Last Out.
This means that the first item added to the stack will be the last one popped out of the stack.

LIFO or Last In First Out.
That is the opposite of above. The last item added will be the first popped off.

Push O(1)
Pushing a Node onto a stack will always be an O(1) operation. This is because it takes the same amount of time no matter how many Nodes (n) you have in the stack.

When adding a Node, you push it into the stack by assigning it as the new top, with its next property equal to the original top.

Given pseudo code for a push from reading:
```
ALOGORITHM push(value)
// INPUT <-- value to add, wrapped in Node internally
// OUTPUT <-- none
   node = new Node(value)
   node.next <-- Top
   top <-- Node
```

Pop O(1)
Popping a Node off a stack is the action of removing a Node from the top. When conducting a pop, the top Node will be re-assigned to the Node that lives below and the top Node is returned to the user.

Typically, you would check isEmpty before conducting a pop. This will ensure that an exception is not raised. Alternately, you can wrap the call in a try/catch block.



[Back](README.md)