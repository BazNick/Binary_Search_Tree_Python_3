import random


class Node:

    """Class to create Node in BST"""

    __slots__ = 'element', 'left_tree', 'right_tree'

    def __init__(self, element, left_tree, right_tree):
        self.element = element
        self.left_tree = left_tree
        self.right_tree = right_tree


class BinarySearchTree:

    """Binary Search Tree class with the following methods:
        - Create tree method;
        - Search element in BST;
        - Remove element in BST;
        - Display in-order element in BST;
        """

    def __init__(self):
        self.root = None

    def create_tree(self, root, e):
        if root is None:
            n = Node(e, None, None)
            root = n
        else:
            if e == root.element:
                print(f"""The element {e} is already exist in the tree!""")
                return
            elif e < root.element:
                root.left_tree = self.create_tree(root.left_tree, e)
            else:
                root.right_tree = self.create_tree(root.right_tree, e)
        return root

    def search_element(self, root, e):
        if root is not None:
            if e == root.element:
                print()
                print(f"""Element {e} is found in the tree!""")
                return True
            elif e < root.element:
                self.search_element(root.left_tree, e)
            else:
                self.search_element(root.right_tree, e)
        else:
            print()
            print(f"""Element {e} is {'not found'.upper()} in the tree""")
            return False

    def removing_element(self, e):
        p = self.root
        temp = p
        while p is not None:
            if e == p.element:
                break
            else:
                if e < p.element:
                    temp = p
                    p = p.left_tree
                else:
                    temp = p
                    p = p.right_tree
        if p is None:
            print(f"""Element {e} is {'not'.upper()} found in the tree""")
        else:
            # case 0 where we don't have any children, in other words it's a leaf node
            if p.left_tree is None and p.right_tree is None:
                if temp.element > p.element:
                    p = None
                    temp.left_tree = p
                    print(f"""Element {e} was deleted from the tree""")
                elif temp.element < p.element:
                    p = None
                    temp.right_tree = p
                    print(f"""Element {e} was deleted from the tree""")
                elif temp == p and p == self.root:
                    p = None
                    self.root = p
                    print(f"""Element {e} was deleted from the tree""")

            # case 1 where we have either right or left child
            # case 1a where we have left child, but no child right
            elif p.left_tree is not None and p.right_tree is None:
                if temp == p and p == self.root:
                    p = p.left_tree
                    self.root = p
                    print(f"""Element {e} was deleted from the tree""")
                else:
                    p = p.left_tree
                    if temp.element > p.element:
                        temp.left_tree = p
                    elif temp.element < p.element:
                        temp.right_tree = p
                    print(f"""Element {e} was deleted from the tree""")

            # case 1b where we have right child, but no left child
            elif p.left_tree is None and p.right_tree is not None:
                if temp == p and p == self.root:
                    p = p.right_tree
                    self.root = p
                    print(f"""Element {e} was deleted from the tree""")
                else:
                    p = p.right_tree
                    if temp.element < p.element:
                        temp.right_tree = p
                    elif temp.element > p.element:
                        temp.left_tree = p
                    print(f"""Element {e} was deleted from the tree""")

            # case 2 where we have two children, right and left
            elif p.left_tree is not None and p.right_tree is not None:
                temp_ptr = p.right_tree
                if temp_ptr.left_tree is None:
                    temp_ptr.element, p.element = p.element, temp_ptr.element
                    p.right_tree = temp_ptr.right_tree
                else:
                    temp_ptr_ptr = temp_ptr
                    while temp_ptr.left_tree is not None:
                        temp_ptr_ptr = temp_ptr
                        temp_ptr = temp_ptr.left_tree
                    if temp_ptr.right_tree is None:
                        temp_ptr.element, p.element = p.element, temp_ptr.element
                        temp_ptr_ptr.left_tree = None
                    else:
                        temp_ptr.element, p.element = p.element, temp_ptr.element
                        temp_ptr_ptr.left_tree = temp_ptr.right_tree
                print(f"""Element {e} was deleted from the tree""")

    def display_in_order(self, root):
        if root is not None:
            self.display_in_order(root.left_tree)
            print(root.element, end=' ')
            self.display_in_order(root.right_tree)


testing_array = [0] * 2000

for i in range(len(testing_array)):
    testing_array[i] = random.randint(-10000, 10000)

# here I use set, to create unique values in BST since BST have to have unique keys
unique_values = list(set(testing_array))

x = BinarySearchTree()
x.root = x.create_tree(x.root, unique_values[0])

for j in range(1, len(unique_values)):
    x.create_tree(x.root, unique_values[j])

x.display_in_order(x.root)
print()
for k in range(len(unique_values)):
    x.removing_element(unique_values[k])

x.display_in_order(x.root)
