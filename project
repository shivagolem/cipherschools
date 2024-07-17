import java.util.Scanner;

class Node {
    int key;
    Node left, right;

    public Node(int item) {
        key = item;
        left = right = null;
    }
}

class BinarySearchTree {
    Node root;

    BinarySearchTree() {
        root = null;
    }

    void insert(int key) {
        root = insertRec(root, key);
    }

    Node insertRec(Node root, int key) {
        if (root == null) {
            root = new Node(key);
            return root;
        }

        if (key < root.key)
            root.left = insertRec(root.left, key);
        else if (key > root.key)
            root.right = insertRec(root.right, key);

        return root;
    }

    void deleteKey(int key) {
        root = deleteRec(root, key);
    }

    Node deleteRec(Node root, int key) {
        if (root == null)
            return root;

        if (key < root.key)
            root.left = deleteRec(root.left, key);
        else if (key > root.key)
            root.right = deleteRec(root.right, key);
        else {
            if (root.left == null)
                return root.right;
            else if (root.right == null)
                return root.left;

            root.key = minValue(root.right);
            root.right = deleteRec(root.right, root.key);
        }

        return root;
    }

    int minValue(Node root) {
        int minValue = root.key;
        while (root.left != null) {
            minValue = root.left.key;
            root = root.left;
        }
        return minValue;
    }

    boolean search(int key) {
        return searchRec(root, key);
    }

    boolean searchRec(Node root, int key) {
        if (root == null)
            return false;

        if (root.key == key)
            return true;

        if (root.key > key)
            return searchRec(root.left, key);

        return searchRec(root.right, key);
    }

    void inorder() {
        inorderRec(root);
    }

    void inorderRec(Node root) {
        if (root != null) {
            inorderRec(root.left);
            System.out.print(root.key + " ");
            inorderRec(root.right);
        }
    }

    public static void main(String[] args) {
        BinarySearchTree tree = new BinarySearchTree();
        Scanner scanner = new Scanner(System.in);
        int choice;

        System.out.println("Please insert between 5 and 7 elements:");

        while (true) {
            System.out.print("Enter the number of elements to insert: ");
            int numElements = scanner.nextInt();

            if (numElements < 5 || numElements > 7) {
                System.out.println("You must insert between 5 and 7 elements. Please try again.");
            } else {
                System.out.println("Enter the elements:");
                for (int i = 0; i < numElements; i++) {
                    int element = scanner.nextInt();
                    tree.insert(element);
                }
                break;
            }
        }

        do {
            System.out.println("\n1. Insert");
            System.out.println("2. Delete");
            System.out.println("3. Search");
            System.out.println("4. Display Inorder");
            System.out.println("5. Exit");
            System.out.print("Enter your choice: ");
            choice = scanner.nextInt();

            switch (choice) {
                case 1:
                    System.out.print("Enter element to insert: ");
                    int element = scanner.nextInt();
                    tree.insert(element);
                    break;
                case 2:
                    System.out.print("Enter element to delete: ");
                    element = scanner.nextInt();
                    tree.deleteKey(element);
                    break;
                case 3:
                    System.out.print("Enter element to search: ");
                    element = scanner.nextInt();
                    if (tree.search(element))
                        System.out.println("Element found");
                    else
                        System.out.println("Element not found");
                    break;
                case 4:
                    System.out.println("Inorder traversal: ");
                    tree.inorder();
                    System.out.println();
                    break;
                case 5:
                    System.out.println("Exiting...");
                    break;
                default:
                    System.out.println("Invalid choice");
            }
        } while (choice != 5);

        scanner.close();
    }
}
