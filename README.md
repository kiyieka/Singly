
class Node:

    def _init_(self, data):
        self.data = data
        self.next = None
        
This is the node class which reepresents a single element in the linked list.
It holds the value off the node and points to the next node in the list, which is  initially set to none.


class LinkedList

    def _init_(self):
        self.head = None
  I now initialised a new linked list.
  self.head points to the first nodein the list.


    def insert_at_end(self, data):
        new_node = Node(data)
        if self.head is None:
            self.head = new_node
            return
        curr = self.head
        while curr.next:
            curr = curr.next
        curr.next = new_node
This is a method that creates a new node with given data.
If the list is empty, the new node then becomes the head.

 def insert_at_start(self, data):
 
        new_node = Node(data)
        new_node.next = self.head
        self.head = new_node
This creates a new node and makes it point to the current head.


    def insert_at_index(self, index, data):
        if index == 0:
            self.insert_at_start(data)
            return
        new_node = Node(data)
        curr = self.head
        count = 0
        while curr and count < index - 1:
            curr = curr.next
            count += 1
        if curr is None:
            raise IndexError("Index out of bounds")
        new_node.next = curr.next
        curr.next = new_node
This is meant to insert a node at a specific index.
if index == 0, we insert at start.
Otherwise, we move curr to the -1 position
Then insert the new node between curr and curr.next.

   def delete_at_index(self, index):
   
        if self.head is None:
            raise IndexError("List is empty")
        if index == 0:
            self.head = self.head.next
            return
        curr = self.head
        count = 0
        while curr.next and count < index - 1:
            curr = curr.next
            count += 1
        if curr.next is None:
            raise IndexError("Index out of bounds")
        curr.next = curr.next.next
This deletes the node at a given index.
If the index is 0, we move the head to the next node.

    def search(self, value):
        curr = self.head
        index = 0
        while curr:
            if curr.data == value:
                return index
            curr = curr.next
            index += 1
        return -1
This goes through the list to find the first node with the matching value.
It returns its index if found and -1 if not.

 def display(self):
 
        curr = self.head
        while curr:
            print(curr.data, end=" -> ")
            curr = curr.next
        print("None")
        
This prints the values of all nodes in the list.
It ends with none to show the end of the list.

if __name__ == "_main_":

    ll = LinkedList()
    ll.insert_at_end(10)
    ll.insert_at_end(20)
    ll.insert_at_start(5)
    ll.insert_at_index(1, 15)

    print("Linked List:")
    ll.display()

    print("Index of 10:", ll.search(10))

    ll.delete_at_index(1)
    print("After deleting at index 1:")
    ll.display()  
This creates an empty linked list then adds 10 and 20 to the end, adds 5 to the start,
15 at index 1 and displays the list.
It deletes the node at index 1, then displays 5 - 10 - 20 - none.
