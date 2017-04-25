## Linked Lists

In the first lesson, we discussed maps. Typically, an interview question won't be about a map, but many questions will require the use of a map. Linked lists are the opposite in this respect. You'll rarely use a linked list to solve a problem (if you need a list you'll probably just use an array), but quite a few problems are about linked lists. For example, you might be asked to determine whether two linked lists are permutation of each other. This is a question about linked lists, but you'll use a map to solve it.

A linked list is a made up of nodes. At their simplest, nodes are objects with two properties. One property is the piece of data associated with the node, aka the value of the node. The next property points or refers to the next node. There is a special node, the head, that is the first in the list. You'll need to maintain a reference to this node. All of the other nodes can be accessed by traversing the "next" pointers. If a linked list contains node that only point to the next node, it is called a singly linked list. If a linked list contains node that also point to the previous node, it is called a doubly linked list. Sometimes a reference to the tail node is also maintained. Given the head, we can always access the tail by traversing the entire list, but this is obviously much slower than just maintaining a reference to the tail node.

```JS

class Node {
  constructor(val) {
    this.val = val;
    this.next = null;
  }
}

class LinkedList {
  constructor () {
    this.head = null;
  }
  
  isEmpty() {
    return this.head === null;
  }
  
  getTailNode() {
    let node = this.head;
    while (node.next !== null) node = node.next;
    return node;
  }
  
  getNode(i) {
    let node = this.head;
    while (node.next !== null && --i >= 0) node = node.next;
    if (i > -1) return -1;
    else return node;
  }
  
  addNode(val, i) {
    if (i === 0) {
      const oldHead = this.head;
      this.head = new Node(val);
      this.head.next = oldHead;
    } else {
      const nodeBefore = getNode(i - 1);
      const oldNext = nodeBefore.next;
      nodeBefore.next = new Node(val);
      nodeBefore.next.next = oldNext;
    }
  }
  
  addNodeToEnd(val) {
    if (this.isEmpty()) this.head = new Node(val);
    else this.getTailNode().next = new Node(val);
  }
  
  removeNode(i) {
    const nodeToRemove = this.getNode(i);
    if (i === 0) {
      this.head = nodeToRemove.next;
    } else {
      const nodeBefore = getNode(i - 1);
      nodeBefore.next = nodeBefore.next.next;
    }
  }
}


```

Some common linked list questions: Reverse a linked list (Leetcode #206), determine if a linked list has a cycle in it (Leetcode #141), find the nth node from the end, delete a (non-tail) node with access to only that node (Leetcode #237).

Also good to be able to compare linked list and array with respect to time complexity of operators.
