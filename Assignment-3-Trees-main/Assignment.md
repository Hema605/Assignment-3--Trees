# Assignment-3-Trees
Assignment-3: Trees
#1----------Implement Binary tree
class Node:
    def __init__(self,key):
        self.left = None
        self.right = None
        self.val = key
        
        
 #2-----------Find height of a given tree
 class Node:
 
    # Constructor to create a new node
    def __init__(self, data):
        self.data = data
        self.left = None
        self.right = None
 
# Compute the "maxDepth" of a tree -- the number of nodes
# along the longest path from the root node down to the
# farthest leaf node
 
 
def maxDepth(node):
    if node is None:
        return 0
 
    else:
 
        # Compute the depth of each subtree
        lDepth = maxDepth(node.left)
        rDepth = maxDepth(node.right)
 
        # Use the larger one
        if (lDepth > rDepth):
            return lDepth+1
        else:
            return rDepth+1
 
 
# Driver program to test above function
root = Node(1)
root.left = Node(2)
root.right = Node(3)
root.left.left = Node(4)
root.left.right = Node(5)
 
 
print("Height of tree is %d" % (maxDepth(root)))



#3------------Perform Pre-order, Post-order, In-order traversal
class Node:
    def __init__(self, x):
        self.data = x
        self.left = None
        self.right = None
 
# Function to print all nodes of a
# binary tree in Preorder, Postorder
# and Inorder using only one stack
def allTraversal(root):
   
    # Stores preorder traversal
    pre = []
 
    # Stores inorder traversal
    post = []
 
    # Stores postorder traversal
    inn = []
 
    # Stores the nodes and the order
    # in which they are currently visited
    s = []
 
    # Push root node of the tree
    # into the stack
    s.append([root, 1])
 
    # Traverse the stack while
    # the stack is not empty
    while (len(s) > 0):
 
        # Stores the top
        # element of the stack
        p = s[-1]
        #del s[-1]
 
        # If the status of top node
        # of the stack is 1
        if (p[1] == 1):
 
            # Update the status
            # of top node
            s[-1][1] += 1
 
            # Insert the current node
            # into preorder, pre[]
            pre.append(p[0].data)
 
            # If left child is not NULL
            if (p[0].left):
 
                # Insert the left subtree
                # with status code 1
                s.append([p[0].left, 1])
 
        # If the status of top node
        # of the stack is 2
        elif (p[1] == 2):
 
            # Update the status
            # of top node
            s[-1][1] += 1
 
            # Insert the current node
            # in inorder, in[]
            inn.append(p[0].data);
 
            # If right child is not NULL
            if (p[0].right):
 
                # Insert the right subtree into
                # the stack with status code 1
                s.append([p[0].right, 1])
 
        # If the status of top node
        # of the stack is 3
        else:
 
            # Push the current node
            # in post[]
            post.append(p[0].data);
 
            # Pop the top node
            del s[-1]
 
    print("Preorder Traversal: ",end=" ")
    for i in pre:
        print(i,end=" ")
    print()
 
    # Printing Inorder
    print("Inorder Traversal: ",end=" ")
 
    for i in inn:
        print(i,end=" ")
    print()
 
    # Printing Postorder
    print("Postorder Traversal: ",end=" ")
 
    for i in post:
        print(i,end=" ")
    print()
 
 
# Driver Code
if __name__ == '__main__':
 
    # Creating the root
    root = Node(1)
    root.left = Node(2)
    root.right = Node(3)
    root.left.left = Node(4)
    root.left.right = Node(5)
    root.right.left = Node(6)
    root.right.right = Node(7)
 
    # Function call
    allTraversal(root)
    
    
    
 
#4--------------Function to print all the leaves in a given binary tree
class Node:
   
    def __init__(self, data):
        self.data = data
        self.left = None
        self.right = None
 
# Function to print leaf
# nodes from left to right
def printLeafNodes(root: Node) -> None:
 
    # If node is null, return
    if (not root):
        return
 
    # If node is leaf node,
    # print its data
    if (not root.left and
        not root.right):
        print(root.data,
              end = " ")
        return
 
    # If left child exists,
    # check for leaf recursively
    if root.left:
        printLeafNodes(root.left)
 
    # If right child exists,
    # check for leaf recursively
    if root.right:
        printLeafNodes(root.right)
 
# Driver Code
if __name__ == "__main__":
 
    # Let us create binary tree shown in
    # above diagram
    root = Node(1)
    root.left = Node(2)
    root.right = Node(3)
    root.left.left = Node(4)
    root.right.left = Node(5)
    root.right.right = Node(8)
    root.right.left.left = Node(6)
    root.right.left.right = Node(7)
    root.right.right.left = Node(9)
    root.right.right.right = Node(10)
 
    # print leaf nodes of the given tree
    printLeafNodes(root)
    
    
    
    
 #5------------   Implement BFS (Breath First Search) and DFS (Depth First Search)
 from collections import defaultdict
 
# This class represents a directed graph
# using adjacency list representation
class Graph:
 
    # Constructor
    def __init__(self):
 
        # default dictionary to store graph
        self.graph = defaultdict(list)
 
    # function to add an edge to graph
    def addEdge(self,u,v):
        self.graph[u].append(v)
 
    # Function to print a BFS of graph
    def BFS(self, s):
 
        # Mark all the vertices as not visited
        visited = [False] * (max(self.graph) + 1)
 
        # Create a queue for BFS
        queue = []
 
        # Mark the source node as
        # visited and enqueue it
        queue.append(s)
        visited[s] = True
 
        while queue:
 
            # Dequeue a vertex from
            # queue and print it
            s = queue.pop(0)
            print (s, end = " ")
 
            # Get all adjacent vertices of the
            # dequeued vertex s. If a adjacent
            # has not been visited, then mark it
            # visited and enqueue it
            for i in self.graph[s]:
                if visited[i] == False:
                    queue.append(i)
                    visited[i] = True
 
# Driver code
 
# Create a graph given in
# the above diagram
g = Graph()
g.addEdge(0, 1)
g.addEdge(0, 2)
g.addEdge(1, 2)
g.addEdge(2, 0)
g.addEdge(2, 3)
g.addEdge(3, 3)
 
print ("Following is Breadth First Traversal"
                  " (starting from vertex 2)")
g.BFS(2)




#6----------Find sum of all left leaves in a given Binary Tree
class Node:
    # Constructor to create a new Node
    def __init__(self, key):
        self.key = key
        self.left = None
        self.right = None
 
# A utility function to check if a given node is leaf or not
def isLeaf(node):
    if node is None:
        return False
    if node.left is None and node.right is None:
        return True
    return False
 
# This function return sum of all left leaves in a
# given binary tree
def leftLeavesSum(root):
 
    # Initialize result
    res = 0
     
    # Update result if root is not None
    if root is not None:
 
        # If left of root is None, then add key of
        # left child
        if isLeaf(root.left):
            res += root.left.key
        else:
            # Else recur for left child of root
            res += leftLeavesSum(root.left)
 
        # Recur for right child of root and update res
        res += leftLeavesSum(root.right)
    return res
 
# Driver program to test above function
 
# Let us construct the Binary Tree shown in the above function
root = Node(20)
root.left = Node(9)
root.right = Node(49)
root.right.left = Node(23)       
root.right.right = Node(52)
root.right.right.left = Node(50)
root.left.left = Node(5)
root.left.right = Node(12)
root.left.right.right = Node(12)
print ("Sum of left leaves is", leftLeavesSum(root))



#7------------Find sum of all nodes of the given perfect binary tree
def SumNodes(l):
     
    # no of leaf nodes
    leafNodeCount = pow(2, l - 1)
 
    # list of vector to store nodes of
    # all of the levels
    vec = [[] for i in range(l)]
 
    # store the nodes of last level
    # i.e., the leaf nodes
    for i in range(1, leafNodeCount + 1):
        vec[l - 1].append(i)
 
    # store nodes of rest of the level
    # by moving in bottom-up manner
    for i in range(l - 2, -1, -1):
        k = 0
 
        # loop to calculate values of parent nodes
        # from the children nodes of lower level
        while (k < len(vec[i + 1]) - 1):
 
            # store the value of parent node as
            # Sum of children nodes
            vec[i].append(vec[i + 1][k] +
                          vec[i + 1][k + 1])
            k += 2
 
    Sum = 0
 
    # traverse the list of vector
    # and calculate the Sum
    for i in range(l):
        for j in range(len(vec[i])):
            Sum += vec[i][j]
 
    return Sum
 
# Driver Code
if __name__ == '__main__':
    l = 3
 
    print(SumNodes(l))
    
    
    
#8-----------    Count subtress that sum up to a given value x in a binary tree
class getNode:
    def __init__(self, data):
         
        # put in the data
        self.data = data
        self.left = self.right = None
         
# function to count subtrees that
# Sum up to a given value x
def countSubtreesWithSumX(root, count, x):
     
    # if tree is empty
    if (not root):
        return 0
 
    # Sum of nodes in the left subtree
    ls = countSubtreesWithSumX(root.left,
                               count, x)
 
    # Sum of nodes in the right subtree
    rs = countSubtreesWithSumX(root.right,
                               count, x)
 
    # Sum of nodes in the subtree
    # rooted with 'root.data'
    Sum = ls + rs + root.data
 
    # if true
    if (Sum == x):
        count[0] += 1
 
    # return subtree's nodes Sum
    return Sum
 
# utility function to count subtrees
# that Sum up to a given value x
def countSubtreesWithSumXUtil(root, x):
     
    # if tree is empty
    if (not root):
        return 0
 
    count = [0]
 
    # Sum of nodes in the left subtree
    ls = countSubtreesWithSumX(root.left,
                               count, x)
 
    # Sum of nodes in the right subtree
    rs = countSubtreesWithSumX(root.right,
                               count, x)
 
    # if tree's nodes Sum == x
    if ((ls + rs + root.data) == x):
        count[0] += 1
 
    # required count of subtrees
    return count[0]
 
# Driver Code
if __name__ == '__main__':
     
    # binary tree creation    
    #         5
    #         / \
    #     -10     3
    #     / \ / \
    #     9 8 -4 7
    root = getNode(5)
    root.left = getNode(-10)
    root.right = getNode(3)
    root.left.left = getNode(9)
    root.left.right = getNode(8)
    root.right.left = getNode(-4)
    root.right.right = getNode(7)
 
    x = 7
 
    print("Count =",
           countSubtreesWithSumXUtil(root, x))
           
           
#9----------- Find maximum level sum in Binary Tree
from collections import deque
  
# A binary tree node has data, pointer
# to left child and a pointer to right 
# child 
class Node:
      
    def __init__(self, key):
          
        self.data = key
        self.left = None
        self.right = None
  
# Function to find the maximum sum 
# of a level in tree
# using level order traversal
def maxLevelSum(root):
      
    # Base case
    if (root == None):
        return 0
  
    # Initialize result
    result = root.data
      
    # Do Level order traversal keeping
    # track of number
    # of nodes at every level.
    q = deque()
    q.append(root)
      
    while (len(q) > 0):
          
        # Get the size of queue when the 
        # level order traversal for one 
        # level finishes
        count = len(q)
  
        # Iterate for all the nodes in
        # the queue currently
        sum = 0
        while (count > 0):
              
            # Dequeue an node from queue
            temp = q.popleft()
  
            # Add this node's value to current sum.
            sum = sum + temp.data
  
            # Enqueue left and right children of
            # dequeued node
            if (temp.left != None):
                q.append(temp.left)
            if (temp.right != None):
                q.append(temp.right)
                  
            count -= 1    
  
        # Update the maximum node count value
        result = max(sum, result)
  
    return result
      
# Driver code
if __name__ == '__main__':
      
    root = Node(1)
    root.left = Node(2)
    root.right = Node(3)
    root.left.left = Node(4)
    root.left.right = Node(5)
    root.right.right = Node(8)
    root.right.right.left = Node(6)
    root.right.right.right = Node(7)
  
    # Constructed Binary tree is:
    #              1
    #            /   \
    #          2      3
    #        /  \      \
    #       4    5      8
    #                 /   \
    #                6     7    
    print("Maximum level sum is", maxLevelSum(root))
    
    
    
 
 #10-----------Print the nodes at odd levels of a tree
 class newNode:
    def __init__(self, data):
        self.data = data
        self.left = self.right = None
 
def printOddNodes(root, isOdd = True):
     
    # If empty tree
    if (root == None):
        return
 
    # If current node is of odd level
    if (isOdd):
        print(root.data, end = " ")
 
    # Recur for children with isOdd
    # switched.
    printOddNodes(root.left, not isOdd)
    printOddNodes(root.right, not isOdd)
 
# Driver code
if __name__ == '__main__':
    root = newNode(1)
    root.left = newNode(2)
    root.right = newNode(3)
    root.left.left = newNode(4)
    root.left.right = newNode(5)
    printOddNodes(root)
