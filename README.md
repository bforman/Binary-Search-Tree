Binary-Search-Tree
==================

An implemented Binary Search Tree coded in Java. Eclipse was the chosen IDE

//Beginning of code

import java.util.Random;
import java.util.Scanner;

/******************************************************************
 * Program: BST2.java
 * Date: Oct 6, 2011, modified from April 2, 2011
 *
 * Author: Ben Forman : collaborated with Ian Matthews and Nick Araya
 * Version 1.0
 */ 

public class BST 
{
    //                 PRIVATE BinaryNode CLASS
    private static class BinaryNode
    {
        int key;
        BinaryNode left;
        BinaryNode right;

        BinaryNode(int x)
        {
            key = x;
            left = null;
            right = null;
        }

        BinaryNode(int x, BinaryNode lchild, BinaryNode rchild)
        {
            key = x;
            left = lchild;
            right = rchild;
        }

        public void setKey(int theKey)
        {
            key = theKey;
        }

        public void setLeft (BinaryNode leftChild)
        {
            left = leftChild;
        }

        public void setRight (BinaryNode rightChild)
        {
            right = rightChild;
        }

        public BinaryNode getLeft()
        {
            return left;
        }

        public BinaryNode getRight()
        {
            return right;
        }

        public int getKey()
        {
            return key;
        }
    }

    //            BINARY SEARCH TREE FIELDS
    private BinaryNode root;     // reference to the root of the tree 
    int treeSize;           // number of elements in the tree

    public BST()
    {
        root = null;
        treeSize = 0;
    }

    //             BINARY SEARCH TREE METHODS
    public int size()
    {
        return treeSize;
    }

    public boolean isEmpty()
    {
        return root == null;
    }

    // MENU ITEM #1 and #2
    public void insert(int item)
    {
        root = insert(item,root);
        treeSize++;
    }

    // MENU ITEM #3
    public void printInOrder()
    {
        printInOrder(root);       
    }

    // MENU ITEM #4
    public int height()
    {
        return height(root);
    }

    // MENU ITEM #5
    public boolean contains(int item)
    {
        return find(item, root);
    }

    // MENU ITEM #6
    public int sumLeaves()
    {
        return sumLeaves(root);
    }

    // MENU ITEM #7
    public int countLeaves()
    {
        return countLeaves(root);
    }

    // MENU ITEM #8
    public int sumNodes()
    {
        return sumNodes(root);
    }

    // MENU ITEM #9
    public int countOdds()
    {
        return countOdds(root);
    }

    // MENU ITEM #10
    public void printPreOrder()
    {
        printPreOrder(root);
    }

    // MENU ITEM #11
    public void printPostOrder()
    {
        printPostOrder(root);
    }

    // MENU ITEM #12
    public void printInReverse()
    {
        printInReverse(root);
    }

    // MENU ITEM #13
    public int countTwoChildren()
    {
        return countTwoChildren(root);
    }

    // MENU ITEM #14
    public int findMin()
    {
        return findMin(root);
    }

    // MENU ITEM #15
    public int findMax()
    {
        // STUB TO FILL IN: returns zero for now
        // not recursive
        return 0;
    }

    // MENU ITEM #16
    public int secondLargest()
    {
        // You may make this iterative or recursive
        // If you make it recursive, then you need to add the method 
        return 0;
    }

    // MENU ITEM #17
    public boolean remove(int num)
    {
        // You may make this iterative or recursive
        // If you make it recursive, then you need to add the method 
        // Do not forget to update the  treeSize
        return false;
    }

    // MENU ITEM #18
    public int findZigZagLength()
    {
        // You may make this iterative or recursive
        // If you make it recursive, then you need to add the method 
        return 0;
    }

    // MENU ITEM #19
    public void clear()
    {
        clear(root);
        root = null;
    }


    // PRIVATE METHOD: Menu #1 and 2:
    private BinaryNode insert(int item, BinaryNode t)
    {
        if (t == null)   
            return new BinaryNode(item);
        if (t.key < item)
            t.right = insert(item, t.right);
        else if (t.key > item)
            t.left = insert(item, t.left);
        // does not insert duplicates
        return t;
    }   

    // PRIVATE METHOD: Menu #3:
    private void printInOrder(BinaryNode t)
    {
        if (t != null) {
            printInOrder(t.left);
            System.out.println (t.key);
            printInOrder(t.right);
        }
    }

    // Menu #4: height of singleton  is 0, 
    //          height of empty tree is -1.
    private int height(BinaryNode t)
    {
        if (t == null)
            return -1;
        int leftHeight = height(t.left);
        int rightHeight = height(t.right);
        if (leftHeight >= rightHeight)
            return 1 + leftHeight;
        return 1 + rightHeight;
    }

    // Menu #5
    private boolean find (int item, BinaryNode t)
    {
        if (t == null)
            return false;
        if (t.key == item)
            return true;
        if (t.key < item)
            return find (item, t.right);
        return find (item, t.left);
    }

    // MENU ITEM #6
    private int sumLeaves(BinaryNode t)
    {
        if (t == null)
        {
            return 0;
        }
        int x = sumLeaves(t.left);
        int y = sumLeaves(t.right);
        if (t.left == null && t.right == null)
        {
            return y + t.key;
        }
        else
        {
            return x + y;
        }
    }

    // MENU ITEM #7
    private int countLeaves(BinaryNode t)
    {
        if (t == null)
        {
            return 0;
        }
        int x = countLeaves(t.left);
        int y = countLeaves(t.right);
        if (t.left == null && t.right == null)
        {
            return 1;
        }
        else
        {
            return x + y;
        }
    }

    // MENU ITEM #8
    private int sumNodes(BinaryNode t)
    {
        if (t == null)
        {
            return 0;
        }
        return t.key + sumNodes(t.left) + sumNodes(t.right);

    }

    // MENU ITEM #9
    private int countOdds(BinaryNode t)
    {
        if (t == null)
        {
            return 0;
        }
        int x = countOdds(t.left);
        int y = countOdds(t.right);
        if (t.key % 2 ==1)
        {
            return 1 + x + y;
        }

        return x + y;
    }

    // MENU ITEM #10
    private void printPreOrder(BinaryNode t)
    {
        if (t != null)
        {
            System.out.println(t.key);
            printPreOrder(t.left);
            printPreOrder(t.right);
        }
        return;
    }

    // MENU ITEM #11
    private void printPostOrder(BinaryNode t)
    {
        if (t != null)
        {
            printPostOrder(t.left);
            printPostOrder(t.right);
            System.out.println(t.key);
        }
        return;
    }

    // MENU ITEM #12
    private void printInReverse(BinaryNode t)
    {
        if (t != null)
        {
            printInReverse(t.right);
            System.out.println(t.key);
            printInReverse(t.left);
        }
    }

    // MENU ITEM #13
    private int countTwoChildren(BinaryNode t)
    {
        if (t == null)
        {
            return 0;
        }
        if (t.getLeft() != null && t.getRight() != null)
        {
            return countTwoChildren(t.left) + countTwoChildren(t.right);
        }
        else if (t.left != null && t.right == null)
        {
            return 1 + countTwoChildren(t.left);
        }
        else if (t.left == null && t.right != null)
        {
            return 1 + countTwoChildren(t.right);
        }
        return 0;
    }

    // MENU ITEM #14
    private int findMin(BinaryNode t)
    {
        if (t != null)
        {
            if (t.left == null)
            {
                return t.key;
            }
            return findMin(t.left);
        }
        return 0;
    }

    // MENU ITEM #19
    private void clear(BinaryNode t)
    {
        if (t == null) return;
        if (t.left != null) {
            clear(t.left);
            t.left = null;
        }
        if (t.right != null) {
            clear(t.right);
            t.right = null;
        }
    }


    public static void main(String [] args)
    {
        BST tree = new BST();
        int howMany, num;
        Random rand = new Random();
        Scanner scan = new Scanner(System.in);

        int choice = menu(scan);
        while (choice < 20) {
            switch (choice)
            {
                case 1: System.out.print ("How many random integers: ");
                howMany = scan.nextInt();
                for (int i = 0; i < howMany; i++)
                    tree.insert(rand.nextInt());
                break;
                case 2: System.out.print ("How many integers: ");
                howMany = scan.nextInt();
                for (int i = 1; i <= howMany; i++) {
                    System.out.print ("Enter number " + i + ".  :");
                    num = scan.nextInt();
                    tree.insert(num);
                }
                break;
                case 3: tree.printInOrder();
                break;
                case 4: System.out.println ("Height " + tree.height());
                break;
                case 5: System.out.print ("Enter number to look for: " ); 
                num = scan.nextInt();
                if (tree.contains(num)) 
                    System.out.println (num + " is there.");     
                else
                    System.out.println (num + " isn't there.");     
                break;
                case 6: System.out.println ("The sum of the leaves is " + 
                        tree.sumLeaves());
                break;
                case 7: System.out.println ("There are " + 
                        tree.countLeaves() + " leaves.");
                break;
                case 8: System.out.println ("The sum of the nodes is " + 
                        tree.sumNodes());
                break;
                case 9: System.out.println ("There are " + 
                        tree.countOdds() + " odd integers.");
                break;
                case 10: tree.printPreOrder();
                break;
                case 11: tree.printPostOrder();
                break;
                case 12: tree.printInReverse();
                break;
                case 13: System.out.println ("There are " + 
                        tree.countTwoChildren() + " nodes with 2 children.");
                break;
                case 14: System.out.println ("The minimum found recursively " + 
                        " is " + tree.findMin());
                break;
                case 15: System.out.println ("The maximum found iteratively " + 
                        " is " + tree.findMax());
                break;
                case 16: System.out.println ("The second largest is " + 
                        + tree.secondLargest());
                break;
                case 17: System.out.print ("Enter number to remove: "); 
                num = scan.nextInt();
                boolean removed = tree.remove(num);
                if (removed)
                    System.out.println ("It is gone.");
                else
                    System.out.println ("That value is not there.");
                break; 
                case 18: System.out.println ("The zigzag length is " + 
                        + tree.findZigZagLength());
                break;
                case 19: tree.clear();
            }
            System.out.println ("Enter zero to continue: ");
            num = scan.nextInt();
            choice = menu(scan); 
        }
    }

    public static int menu(Scanner cin)
    {
        int choice=0, result;

        System.out.println("**************************************************");
        System.out.println("           BST Test Methods  ");
        System.out.println("**************************************************");
        System.out.println("       1.  Insert Some Random Numbers #1 ");
        System.out.println("       2.  Insert Some Specific Numbers");
        System.out.println("       3.  Print the Tree in Order");
        System.out.println("       4.  Determine the Tree Height ");
        System.out.println("       5.  Find a Specific Number");
        System.out.println("       6.  Sum the Leaves ***");
        System.out.println("       7.  Count the Leaves ***");
        System.out.println("       8.  Sum the Nodes in the Tree ***");
        System.out.println("       9.  Count the Number of Odd Nodes ***");
        System.out.println("      10.  Print the tree in Pre-order ***");
        System.out.println("      11.  Print the tree in Post-order ***");
        System.out.println("      12.  Print the Nodes in Reverse order ***"); 
        System.out.println("      13.  Count the Nodes with 2 Children ***");
        System.out.println("      14.  Return the Minimum Item ***");
        System.out.println("      15.  Return the Maximum Item");
        System.out.println("      16.  Return the 2nd Largest");
        System.out.println("      17.  Remove a specific Number");
        System.out.println("      18.  Extra credit: compute zigzag length"); 
        System.out.println("      19.  Clear Tree"); 
        System.out.println("      20.  Quit ");
        System.out.println("**************************************************");

        System.out.print("\n\nEnter your choice: ");
        choice = cin.nextInt();

        if (choice < 1 || choice > 20)
            choice = 20;

        return choice;
    }
}

