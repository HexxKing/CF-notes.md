> a linked list is usually efficient when it comes to adding and removing most elements, but can be very slow to search and find a single element.

# [Linked Lists](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-05/resources/singly_linked_list.html)
- a Linked list is a data structure that contains a sequence of Nodes that are connected or linked to each other
  - each node references the next node in the link
  - a node is the individual items (containg data) that live in a linked list
  - each node contains a property called Next, which contains the reference to the next node.
  - Head is the first node in a linked list
  - Current is the current node being looked at
    - When traversing, you typically reset the current to the head to guarantee you are starting from the beginning of the linked list.
- A Singly linked list means that there is only one reference, and the reference points to the Next node in a linked list.
- A Doubly linked list means that there is a reference to both the Next and Previous node.
- When constructing your code, a few things to keep in mind.
  - When making your Node class, consider requiring a value to be passed in to require that each node has a value.
  - When making a Linked List, you may want to require that at least one node gets passed in upon instantiation. This first node is what your Head and Current will point too.

### Traversal
- while() loop allows us to continually check that the Next node in the list is not null.   
  - If you try to traverse on a node that is null, a NullReferenceException is raised and our program will crash/end
  - dont use foreach or for loops
- We will know we are at the last node in the linked list because the current node will be null.

### Big O
- The Big O of time for Includes would be O(n). 
  - This is because, at its worse case, the node we are looking for will be the very last node in the linked list. n represents the number of nodes in the linked list.
- The Big O of space for Includes would be O(1). 
  - This is because there is no additional space being used than what is already given to us with the linked list input.

### Adding a Node
-  If we want to add a node with an O(1) efficiency, we have to replace the current Head of the linked list with the new node, without losing the reference to the next node in the list.
- the required steps to add a new node with an O(1) efficiency:
  - Set Current equal to Head. 
  - We can then instantiate the new node that we are adding. The values passed in as arguments into the Add() method will define what the value of the Node will be.
  - newNode.Next by default is set to null. We want to set newNode.Next property to the same location that the Head node is pointing towards. Because Head is just a reference type, we will be assigning it to the same allocation in memory as the node it is pointing too. In this case, it’s Node1.
  - At this point in the program we now “technically” have newNode at the beginning of the linked list, but we are not done yet. We now have to re-assign where Head is pointing too. Since Node1 is no longer the first node in the list, we want to re-assign Head to point at newNode.
  - re-assign current as well to make sure should any further operation start at the new true start of the linked list.
- Big O: Regardless of the number of Nodes that this linked list has, it will always be a O(1) time and space because it takes the same amount of time to add a new node to the beginning of the list, and no additional resources are being used
- When adding a node to the middle of a linked list, it must re-allocate to make room for the new node.
  - we have to adjust current node.Next to point to the newly created node. We just simply tell Current to change it’s Next to point to the new node.
  - Big O:
    - The time efficiency of this transaction would be O(n) because we could be inserting the new node, worst case scenario, at the end. With n being the number of nodes possible, we would therefore have O(n) time efficiency.
    - Space efficiency would stay at an O(1) because, like before, no additional space is being used allocated outside of what is given to us on the input

### Print Out Nodes
- Much like in the Find, we are creating a while loop to check and make sure we are not at the end of a linked list.

# [What’s a Linked List, Anyway? - Part 1](https://medium.com/basecs/whats-a-linked-list-anyway-part-1-d8b7e6508b9d)
- One characteristic of linked lists is that they are linear data structures, which means that there is a sequence and an order to how they are constructed and traversed.
- The biggest differentiator between arrays and linked lists is the way that they use memory in our machines. 
- Just as characters, numbers, words, sentences require bytes of memory to represent them, so do data structures.
  - When an Array is created, our computer needs n bytes of fre  memory, one byte next to the another, all together, in one place.
  - Linked lists don’t need to take up a single block of memory; instead, the memory that they use can be scattered throughout.
  - The fundamental difference between arrays and linked lists is that arrays are static data structures, while linked lists are dynamic data structures. 
    - A static data structure needs all of its resources to be allocated when the structure is created; this means that even if the structure was to grow or shrink in size and elements were to be added or removed, it still always needs a given size and amount of memory.
    - a dynamic data structure doesn’t need a set amount of memory to be allocated in order to exist, and its size and shape, and the amount of memory it needs can change as well.
- Nearly all linked lists must have a head, because this is effectively the only entry point to the list and all of its elements, and without it, you wouldn’t know where to start! 
- The end of the list isn’t a node, but rather a node that points to null, or an empty value.
- A single node is also pretty simple. It has just two parts: data, or the information that the node contains, and a reference to the next node.
  - Because a single node has the “address” or a reference to the next node, they don’t need to live right next to one another, the way that the elements have to in an array.
  - This is also the explanation for why linked lists can grow and shrink dynamically during a program’s execution. Adding or removing a node with a linked list becomes as simple as rearranging some pointers, rather than copying over the elements of an array!
  - Doubly linked lists: everything requires space and memory, so if our node had to store two reference pointers instead of just one, that would be another thing to consider.
- A circular linked list has a node that acts as the tail of the list (rather than the conventional head node), and the node after the tail node is the beginning of the list. 
  - This organization structure makes it really easy to add something to the end of the list, because you can begin traversing it at the tail node, as the first element and last element point to one another.

# [What’s a Linked List, Anyway? - Part 2](https://medium.com/basecs/whats-a-linked-list-anyway-part-2-131d96f71996)
- One way to think about Big O notation is a way to express the amount of time that a function, action, or algorithm takes to run based on how many elements we pass to that function.
  - O (referred to as just “O” or sometimes as “order”), and a variable n, where n is the size of the input (think back to our our ten, thousands, or millions of numbers).
  - An O(n) function is linear, which means that as our input grows (from ten numbers, to ten thousand, to ten million), the space and time that we need to run that algorithm grows linearly.
  - an O(n²) function, which clearly takes exponentially more time and memory the more elements that you have. 
- all we need to do in order to add something to our linked list is figure out which pointer needs to point to where.
  - First, we find the head node of the linked list.
  - Next, we’ll make our new node, and set its pointer to the current first node of the list.
  - Lastly, we rearrange our head node’s pointer to point at our new node.
    - If we accidentally end up doing step 3 before step 2, we end up in a bit of a mess. The reason being that if we point our head node to the new node before connecting the new, still-to-be-inserted, node to the rest of the list that comes afterwards, we’d end up in a cyclical structure, with only two nodes, and we’d effectively lose all of our other data in the list. 
- Inserting an element at the end of a linked list takes the same steps as inserting at the beginning, however we’re adding something after the last node and we will need to find that last node. We’ll need to traverse through the entire linked list to find it. Linked lists are distributed, non-contiguous in memory, which means that each node will live at a totally different “address” in memory. So traversing is going to take time — it’s going to take more time with the more nodes we have. Big O Notation = O(n)
- If you ever find yourself having to do something that requires a lot of traversal, iteration, or quick index-level access, a linked list could be your worst enemy. In those situations, an array might be a better solution, since you can find things quickly (a single chunk of allocated memory), and you can use an index to quickly retrieve a random element in the middle or end of the list without having to take the time to traverse through the whole entire thing.

