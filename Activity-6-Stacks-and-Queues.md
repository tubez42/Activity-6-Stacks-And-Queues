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
















