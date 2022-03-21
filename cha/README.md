| [Home](..) |[TPT Notes](../not)| [Challenges](.) | [Test Prep Plans](../pln) |[Review Tickets](../rev)|

# TPT Challeges

## Week 1

```Java
import java.util.Iterator;

class Queue<T> implements Iterable<T>{
    LinkedList<T> head, tail;

    public void add(T data){
        LinkedList<T> t = new LinkedList<>(data, null);
        if(this.head == null){
            this.head = this.tail = t ;
        }
        else{
            this.tail.setNextNode(t);
            t.setPrevNode(this.tail);
            this.tail = t;
        }
    }

    public void delete() {
        LinkedList<T> n = this.head.getNext();
        if (n != null) {
            n.setPrevNode(null);
            this.head = n;
        }else{
            this.head= this.tail= null;
        }
    }

    public LinkedList<T> getHead()
    {
        return this.head;
    }

    public LinkedList<T> getTail()
    {
        return this.tail;
    }

    /**
     *  Returns the iterator object.
     *
     * @return  this, instance of object
     */
    @Override
    public Iterator<T> iterator() {
        return new QueueIterator<>(this);
    }

    public static void main(String[] args){
        // Create iterable Queue of Words
        Object[] words = new String[] { "seven", "slimy", "snakes", "sallying", "slowly", "slithered", "southward"};
        QueueManager qWords = new QueueManager("Words", words );
        qWords.printQueue();
        qWords.deleteList();



    }

}
```
```java
import java.util.Iterator;

/**
 * Queue Iterator
 *
 * 1. "has a" current reference in Queue
 * 2. supports iterable required methods for next that returns a data object
 */
class QueueIterator<T> implements Iterator<T> {
    LinkedList<T> current;  // current element in iteration

    // QueueIterator is intended to the head of the list for iteration
    public QueueIterator(Queue<T> q) {
        current = q.getHead();
    }

    // hasNext informs if next element exists
    public boolean hasNext() {
        return current != null;
    }

    // next returns data object and advances to next position in queue
    public T next() {
        T data = current.getData();
        current = current.getNext();
        return data;
    }
}

```
```java
class QueueManager<T> {
    // queue data
    private final String name; // name of queue
    private int count = 0; // number of objects in queue
    public final Queue<T> queue = new Queue<>(); // queue object

    /**
     *  Queue constructor
     *  Title with empty queue
     */
    public QueueManager(String name) {
        this.name = name;
    }

    /**
     *  Queue constructor
     *  Title with series of Arrays of Objects
     */
    public QueueManager(String name, T[]... seriesOfObjects) {
        this.name = name;
        this.addList(seriesOfObjects);
    }

    /**
     * Add a list of objects to queue
     */
    public void addList(T[]... seriesOfObjects) {
        for (T[] objects: seriesOfObjects)
            for (T data : objects) {
                this.queue.add(data);
                printQueue();
                this.count++;
            }
    }

    /**
     * Print any array objects from queue
     */
    public void printQueue() {
        System.out.println(this.name + " count: " + count);
        System.out.print(this.name + " data: ");
        for (T data : queue)
            System.out.print(data + " ");
        System.out.println();
    }

    public void deleteList(){
        while (this.queue.getHead() != null) {
            this.queue.delete();
            this.count--;
            printQueue();
        }
    }
}
```

## Week 0

* [Repl](https://replit.com/@Navoditmah/menu)

```java
import java.util.ArrayList;
import java.util.Arrays;
import java.util.Scanner;

public class Main {

   /* public static String[] New(ArrayList<String> = menu){
        System.out.println("Add new project to the menu list");
        Scanner myObj = new Scanner(System.in);
        String newItem;
        //System.out.println("Enter username");
        newItem = myObj.nextLine();
        System.out.println(newItem);
        menu[menu.length] = newItem;

        return menu;
    }  */

    public static void main(String[] args){
        System.out.println("Hello World");
        ArrayList<String> menu = new ArrayList<>(Arrays.asList("Exit", "Matrix"));
        System.out.println("-------------------------");
        System.out.println("Choose from these choices");
        System.out.println("-------------------------");
        for(int i=0; i<menu.size(); i++){
            System.out.println(i +". "+ menu.get(i));
        }
        System.out.println("-------------------------");
    }
}

```
``` java
public class Matrix {

    private final int[][] matrix;

    // store matrix
    public Matrix(int[][] matrix) {
        this.matrix = matrix;
    }

    // Hack: create toString method using nested for loops to format output of a matrix


    // declare and initialize a matrix for a keypad
    static int[][] keypad() {
        return new int[][]{ { 1, 2, 3 }, { 4, 5, 6 }, { 7, 8, 9 }, {-1, 0, -1} };
    }

    // declare and initialize a random length arrays
    static int[][] numbers() {
        return new int[][]{ { 0, 1 },
                { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 },
                { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15 } };
    }

    // tester method for matrix formatting
    public static void main(String[] args) {
        Matrix m0 = new Matrix(keypad());
        System.out.println("Keypad:");
        for(int i = 0; i<3; i++){
            for(int j = 0; j<3; j++){
                System.out.print(m0.matrix[j][i]);
            }
            System.out.println("");
        }

        // System.out.println(m0);

        Matrix m1 = new Matrix(numbers());
        System.out.println("Numbers Systems:");
        System.out.println(m1);
    }

}

```
