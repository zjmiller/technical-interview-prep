There are two main ways to traverse through a tree: depth-first-search or breadth-first-search. 

DFS is recursive, and involves deeply searching a node's first child before moving on to the second, third, etc. When you're applying DFS to a binary tree, the main decision point with DFS is the relative order in which: (1) look at the current node, (2) apply DFS to the left child, and (3) apply DFS to the right child. When we talk about binary search trees, we'll use the terms pre-order, in-order, and post-order traversal: pre-order traversal operators (1), (2), (3); in-order traversal (2), (1), (3); and post-order traversal (2), (3), (1).

BFS, on the other hand, searches all of a node's children before moving onto the children's children. BFS is almost always implemented using a queue. First add the starting node to the queue, then start a loop where you dequeue, visit the dequeued node, and queue the node's children. Continue this loop until the queue is empty.
