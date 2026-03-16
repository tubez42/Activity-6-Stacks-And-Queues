# Activity 6 Stacks and Queues

##  1. Using Figure 17 as a model, in the book Data Structures in C++, illustrate the result of each operation in the sequence PUSH(S,4), PUSH(S,1), PUSH(S,3), POP(S), PUSH(S,8), and POP(S) on an initially empty stack [1..6].
<img width="538" height="524" alt="Screenshot 2026-03-10 130203" src="https://github.com/user-attachments/assets/6f504bce-0cd3-42d6-8442-20c47543c6c7" />
Is our reference model for our example.

### PUSH (S,4)
<img width="882" height="44" alt="image" src="https://github.com/user-attachments/assets/b1d72304-fa6e-4d2c-ab98-2914d2e0a0c2" />

  Our stack starts off as an empty array. We then push on the first item, 4, onto the stack an so it fills the first index spot starting at  index 1.
  
<img width="876" height="47" alt="image" src="https://github.com/user-attachments/assets/2e342692-e978-4ead-8032-750b6e7a6733" />

### PUSH (S,1), PUSH (S,3)
We then have two more push operations these values are sequnetially added to the top of the stack or the left of the array. The new S.top becomes 3 as refering to the index.
 <img width="883" height="54" alt="image" src="https://github.com/user-attachments/assets/3d5ea9c9-67e4-4337-b5f8-8520a795d6a9" />

### POP(S)
The pop command removes the S.top value from the stack and so it becomes the following with S.top = 2.
<img width="880" height="58" alt="image" src="https://github.com/user-attachments/assets/dff7b1f7-cad9-4c03-a1df-1d700186b190" />

### PUSH (S,8)
This pushes a new value of 8 onto the stack and so S.top becomes 3.
<img width="889" height="61" alt="image" src="https://github.com/user-attachments/assets/5d459b21-1b7f-49e4-afef-5edf4a00691e" />

### POP(S)
This command then pops the value of 8 off of the stack and so the new S.top is again 2.
<img width="895" height="65" alt="image" src="https://github.com/user-attachments/assets/da7eb743-33d1-4d23-80c8-49d51f1a7be7" />

## 2.Using Figure 18 as a model, in the book Data Structures in C++, illustrate the result of each operation in the sequence ENQUEUE(Q,4), ENQUEUE(Q,1), ENQUEUE(Q,3), DEQUEUE(Q), ENQUEUE(Q,8), and DEQUEUE(Q) on an initially empty queue Q stored in array Q[1..6].
Here is Fig.18 for reference.

<img width="530" height="513" alt="image" src="https://github.com/user-attachments/assets/5f11dd19-b416-4961-aa3b-053c317729a0" />

Starting with an initally empty with a length of six and index beginning at 1.
<img width="886" height="60" alt="image" src="https://github.com/user-attachments/assets/53fe50ce-a951-4491-8833-5f866c3b9ed4" />

### ENQUEUE(Q,4), ENQUEUE(Q,1), ENQUEUE(Q,3)
The first three actions are all enqueue meaning we'll be appending their values to the tail. When our queue is empty the tail is equalivalent to the head. After our 3 enqueue actions the queue will look like this.
<img width="889" height="52" alt="image" src="https://github.com/user-attachments/assets/47fdcdb0-e442-4c01-aa85-807f029ae198" />

### DEQUEUE(Q)
This action will remove the current head of the queue. Depending on the implementation the remain values can shift or remain in the same place. 
(started having issues with github where I couldn't upload images by pasting them), chose to use an ASCII representation instead.)
```
+-----+-----+-----+-----+-----+-----+
| [1] | [2] | [3] | [4] | [5] | [6] | Index
+-----+-----+-----+-----+-----+-----+
|     |  1  |  3  |     |     |     | Queue
+-----+-----+-----+-----+-----+-----+
```

### ENQUEUE(Q,8)
This action will add a value to the end of the queues tail and take the following index slot in memory. 
```
+-----+-----+-----+-----+-----+-----+
| [1] | [2] | [3] | [4] | [5] | [6] | Index
+-----+-----+-----+-----+-----+-----+
|     |  1  |  3  |  8  |     |     | Queue
+-----+-----+-----+-----+-----+-----+
```
### DEQUEUE(Q)
The next dequeue command will remove the current head of the queue at index 2 and the new head will be established by index 3. 

```
+-----+-----+-----+-----+-----+-----+
| [1] | [2] | [3] | [4] | [5] | [6] | Index
+-----+-----+-----+-----+-----+-----+
|     |     |  3  |  8  |     |     | Queue
+-----+-----+-----+-----+-----+-----+
```

# 3. Rewrite ENQUEUE and DEQUEUE to detect underflow and overflow of a queue. (see Listings 4 & 5 in the book). 

Listing 4 Pseudocode of ENQUEUE(Q,x)
```
Q[Q.tail] = x
if Q.tail == Q.length
    Q.tail = 1
else Q.tail = Q.tail + 1
```
Listing 5 Pseudocode of DEQUEUE(Q)
```
x = Q[Q.head]
if Q.head == Q.length
    Q.head = 1
else Q.head = Q.head + 1
return x
```
Here are their rewrites to detect underflow and overflow of a queue.
ENQUEUE(Q,x)
This checks to see if advancing the queue would make the head equal the tail
```
if Q.head == ((Q.tail mod Q.length) + 1)
    error "overflow"

Q[Q.tail] = x

if Q.tail == Q.length
    Q.tail = 1
else
    Q.tail = Q.tail + 1
```
DEQUEUE(Q)
When dequeuing we risk underflow when the head and tail value become the same by taking away all avilable values from the queue.
```
if Q.head == Q.tail
    error "underflow"

x = Q[Q.head]

if Q.head == Q.length
    Q.head = 1
else
    Q.head = Q.head + 1

return x
```
# 4. A stack allows insertion and deletion of elements at only end, and a queue allows insertion at one end and deletion at the other end, a deque (double-ended queue) allows insertion and deletion at both ends. Write four O(1)-time procedures to insert elements into and delete elements from both ends of a deque implemented by an array.
  In total we need a insert_front insert_rear, delete_front, and delete_rear function with O(1) time meaning we don't wantt to shift any values for the double-ended queue.
```
  INSERT_FRONT(Q, x)
    if Q.head == 1  //check if initial head is at the start of the array
                    //if so, we loop back to the end of the array at index Q.length
        Q.head = Q.length
    else
        Q.head = Q.head - 1  //decrement the head to update its index for the new head

    Q[Q.head] = x   //insert new head
```
```
INSERT_REAR(Q, x)
    if Q.tail == Q.length   //check for wrap around
        Q.tail = 1
    else
        Q.tail = Q.tail + 1   //insert new tail index

    Q[Q.tail] = x  //add value to tail
```
```
DELETE_FRONT(Q)
    if Q.head == Q.tail
        error "underflow"  // Deque is empty

    x = Q[Q.head]

    if Q.head == Q.length   //wrap around handling
        Q.head = 1
    else
        Q.head = Q.head + 1

    return x
```

```
DELETE_REAR(Q)
    if Q.head == Q.tail
        error "underflow"  // Deque is empty

    x = Q[Q.tail]

    if Q.tail == 1
        Q.tail = Q.length //wrap around handling
    else
        Q.tail = Q.tail - 1

    return x
```












