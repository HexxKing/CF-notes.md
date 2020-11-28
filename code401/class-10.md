# [Stacks and Queues](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-10/resources/stacks_and_queues.html)

## Stacks
- Each Node references the next Node in the stack, but does not reference its previous.
- Push - Nodes or items that are put into the stack are pushed
  - Pushing a Node onto a stack will always be O(1) 
  - When adding a Node, you push it into the stack by assigning it as the new top, with its next property equal to the original top
- Pop - Nodes or items that are removed from the stack are popped. When you attempt to pop an empty stack an exception will be raised.
  - O(1)
  - Popping a Node off a stack is the action of removing a Node from the top. 
  - When conducting a pop, the top Node will be re-assigned to the Node that lives below and the top Node is returned to the user.
  - Typically, you would check isEmpty before conducting a pop. This will ensure that an exception is not raised. 
    - Alternately, you can wrap the call in a try/catch block
- Top - This is the top of the stack.
- Peek - When you peek you will view the value of the top Node in the stack. When you attempt to peek an empty stack an exception will be raised.
  - O(1)
  - When conducting a peek, you will only be inspecting the top Node of the stack.
  - We do not re-assign the next property when we peek because we want to keep the reference to the next Node in the stack. This will allow the top to stay the top until we decide to pop.
  - Typically, you would check isEmpty before conducting a peek. This will ensure that an exception is not raised. Alternately, you can wrap the call in a try/catch block.
- IsEmpty - returns true when stack is empty otherwise returns false.
- FILO aka First In Last Out means that the first item added in the stack will be the last item popped out of the stack.
- LIFO aka Last In First Out means that the last item added to the stack will be the first item popped out of the stack.
- the topmost item is denoted as the top. 
  - When you push something to the stack, it becomes the new top. 
  - When you pop something from the stack, you pop the current top and set the next top as top.next

## Queue
- Enqueue - Nodes or items that are added to the queue.
  - When you add an item to a queue, you use the enqueue action. 
  - This is done with an O(1) operation in time because it does not matter how many other items live in the queue (n); it takes the same amount of time to perform the operation.
- Dequeue - Nodes or items that are removed from the queue. 
  - When you remove an item from a queue, you use the dequeue action. 
  - This is done with an O(1) operation in time because it doesn’t matter how many other items are in the queue, you are always just removing the front Node of the queue.
  - Typically, you would check isEmpty before conducting a dequeue. This will ensure that an exception is not raised. 
    - Alternately, you can wrap the call in a try/catch block.
- Front - This is the front/first Node of the queue.
- Rear - This is the rear/last Node of the queue.
- Peek - When you peek you will view the value of the front Node in the queue. If called when the queue is empty an exception will be raised.
- IsEmpty - returns true when queue is empty otherwise returns false.
- FIFO aka First In First Out, means that the first item in the queue will be the first item out of the queue.
- LILO aka Last In Last Out, means that the last item in the queue will be the last item out of the queue.