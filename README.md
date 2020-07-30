# Event-B-Refinement

Each of the following requires the construction of a refinement within Event-B. 
Each of them should have proper invariants, linking the state of the machine being refined to the state of the refinement. 
It should be made sure that the events reflect the events of the machine being refined. 
All the proof of obligations need to be discharged. 

No.1
----------
In the project Progress, the machine Progress tracks the career progress of employees, by partitioning them into three sets. 
It should be refined to maintain a partial function from employees to their employment status as described in the template ProgressR.

No. 2
-----------
In the project Papers, refine the machine Papers so that the set of houses is maintained by a partial function as described in the template PapersR.

No. 3
-----------
A stack is a last-in-first-out queue, which allows elements to be pushed onto the top of the stack, or popped from the top of the stack. 
Such a stack is specified in the project Stack in the machine Stack. The refinement should use an array to record the elements of the stack in order.

No.4
-----------
In the project Buffer, a refinement is to be provided to the machine Buffer, which implements a first-in-first-out queue.

This needs to be achieved by using an array a : 1..maxsize --> ELEMENT to keep track of the contents of the buffer. 
This will also need some other state variables: f, to keep track of the next element to be output, b, to keep track of the point beyond the end of the buffer (i.e. where the next input will be placed)
The contents of the buffer will correspond to the elements of the array between f and b (allowing for wrap-around if b < f because of arithmetic modulo maxsize). 
For example, with maxsize = 10, the buffer containing 3, 5, 4 and 8 may correspond to the array [0,0,0,0,3,5,4,8,0,0] with f = 5 and b = 9. It may also be represented by [4,8,0,0,0,0,0,0,3,5] with f = 9 and b = 3.

The linking invariant will thus link buffer and a as follows: !n.(n:dom(buffer) => buffer(n)=a((n+f-2 mod maxsize)+1))

It will also have to relate f and b to card(buffer).