# JavaScript Merge k Sorted Lists

## Challenge:

You are given an array of `k` linked-lists `lists`, each linked-list is sorted in ascending order.

Merge all the linked-lists into one sorted linked-list and return it.

### 1<sup>st</sup> Example:

`Input: lists = [[1,4,5],[1,3,4],[2,6]]`
<br/>
`Output: [1,1,2,3,4,4,5,6]`
<br/>
`Explanation: The linked-lists are:`
<br/>
`[`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`1->4->5,`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`1->3->4,`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`2->6`
<br/>
`]`
<br/>
`merging them into one sorted list:`
<br/>
`1->1->2->3->4->4->5->6`

### 2<sup>nd</sup> Example:

`Input: lists = []`
<br/>
`Output: []`

### 3<sup>rd</sup> Example:

`Input: lists = [[]]`
<br/>
`Output: []`

### Constraints:

`k == lists.length`
<br/>
`0 <= k <= 10⁴`
<br/>
`0 <= lists[i].length <= 500`
<br/>
`-10⁴ <= lists[i][j] <= 10⁴`
<br/>
`lists[i]` is sorted in ascending order.
<br/>
The sum of `lists[i].length` will not exceed `10⁴`.

## Solution:

`const mergeKLists = (lists) => {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`const queue = new MinPriorityQueue({priority: x => x.val});`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`for (const head of lists) {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`if (head) {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`queue.enqueue(head);`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`}`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`}`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`let result = new ListNode();`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`const head = result;`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`while (!queue.isEmpty()) {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`const { val, next } = queue.dequeue().element;`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`result.next = new ListNode(val);`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`result = result.next;`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`if (next) {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`queue.enqueue(next);`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`}`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`}`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`return head.next;`
<br/>
`};`
<br/>
<br/>

## Explanation:

I've built a function called `mergeKLists` that takes an array of linked lists, `lists`, as input. The purpose of this function is to merge all the linked lists into one sorted linked list and return the head of the merged list.
<br/>

Inside the function, a minimum priority queue called `queue` is created using the `MinPriorityQueue` class. The priority of each element in the queue is determined by its `val` property.
<br/>

A `for...of` loop is used to iterate over each linked list in the `lists` array. Within the loop, the current linked list `head` is checked to see if it is not null or empty.
<br/>

If the `head` is not null, it is enqueued into the `queue` using the `enqueue` method.
<br/>

A new instance of the `ListNode` class called `result` is created. This will be used to store the merged list.
<br/>

The value of `result` is assigned to a new variable called `head`. This variable represents the head of the merged list.
<br/>

A `while` loop is entered that continues until the `queue` is empty.
<br/>

Inside the loop, an element is dequeued from the `queue` using the `dequeue` method. The returned object is destructured to obtain the `val` and `next` properties of the dequeued element.
<br/>

A new instance of the `ListNode` class is created with the value `val` and assigned to the `next` property of `result`.
<br/>

The `result` variable is updated to point to the newly created node.
<br/>

If the `next` property is not null, it means there are more elements in the linked list. In that case, the `next` element is enqueued into the `queue` using the `enqueue` method.
<br/>

Once the `while` loop ends, the `next` property of the `head` variable, which represents the merged list, is returned as the output of the function.
<br/>

In summary, this function merges multiple linked lists into one sorted linked list using a minimum priority queue. It iterates over each linked list, enqueues the non-null heads into the queue, and then dequeues the elements from the queue in sorted order to create the merged list. The head of the merged list is returned as the output of the function.
<br/>
<br/>