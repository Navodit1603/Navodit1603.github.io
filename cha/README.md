| [Home](..) |[TPT Notes](../not)| [Challenges](.) | [Test Prep Plans](../pln) |[Review Tickets](../rev)|

# TPT Challeges


## Week 2

```java
import java.util.ArrayList;
import java.util.HashMap;
import java.util.Map;
import java.util.Stack;

public class Calculator {

    public Calculator(String expression) {
        // original input
        this.expression = expression;

        // parse expression into terms
        this.termTokenizer();

        // place terms into reverse polish notation
        this.tokensToReversePolishNotation();

        // calculate reverse polish notation
        this.rpnToResult();
    }

    private void tokensToReversePolishNotation () {
        // contains final list of tokens in RPN
        this.reverse_polish = new ArrayList<>();

        // stack is used to reorder for appropriate grouping and precedence
        Stack tokenStack = new Stack();
        for (String token : tokens) {
            switch (token) {
                // If left bracket push token on to stack
                case "(":
                    tokenStack.push(token);
                    break;
                case ")":
                    while (tokenStack.size() != 0 && !tokenStack.peek().equals("("))
                    {
                        reverse_polish.add( (String)tokenStack.pop() );
                    }
                    tokenStack.pop();
                    break;
                case "+":
                case "-":
                case "*":
                case "/":
                case "%":
                case "^":
                case "√":
                    // While stack
                    // not empty AND stack top element
                    // and is an operator
                    while (tokenStack.size() != 0 && isOperator((String) tokenStack.peek()))
                    {
                        if ( isPrecedent(token, (String) tokenStack.peek() )) {
                            reverse_polish.add((String)tokenStack.pop());
                            continue;
                        }
                        break;
                    }
                    // Push the new operator on the stack
                    tokenStack.push(token);
                    break;
                default:    // Default should be a number, there could be test here
                    this.reverse_polish.add(token);
            }
        }
        // Empty remaining tokens
        while (tokenStack.size() != 0) {
            reverse_polish.add((String)tokenStack.pop());
        }

    }

    // Helper definition for supported operators
    private final Map<String, Integer> OPERATORS = new HashMap<>();
    {
        // Map<"token", precedence>
        OPERATORS.put("^", 2);
        OPERATORS.put("√",2);
        OPERATORS.put("*", 3);
        OPERATORS.put("/", 3);
        OPERATORS.put("%", 3);
        OPERATORS.put("+", 4);
        OPERATORS.put("-", 4);
    }

    // Helper definition for supported operators
    private final Map<String, Integer> SEPARATORS = new HashMap<>();
    {
        // Map<"separator", not_used>
        SEPARATORS.put(" ", 0);
        SEPARATORS.put("(", 0);
        SEPARATORS.put(")", 0);
    }

    // Test if token is an operator
    private boolean isOperator(String token) {
        // find the token in the hash map
        return OPERATORS.containsKey(token);
    }

    // Test if token is an separator
    private boolean isSeperator(String token) {
        // find the token in the hash map
        return SEPARATORS.containsKey(token);
    }

    // Compare precedence of operators.
    private Boolean isPrecedent(String token1, String token2) {
        // token 1 is precedent if it is greater than token 2
        return (OPERATORS.get(token1) - OPERATORS.get(token2) >= 0) ;
    }


    // Term Tokenizer takes original expression and converts it to ArrayList of tokens
    private void termTokenizer() {
        // contains final list of tokens
        this.tokens = new ArrayList<>();

        int start = 0;  // term split starting index
        StringBuilder multiCharTerm = new StringBuilder();    // term holder
        for (int i = 0; i < this.expression.length(); i++) {
            Character c = this.expression.charAt(i);
            if ( isOperator(c.toString() ) || isSeperator(c.toString())  ) {
                // 1st check for working term and add if it exists
                if (multiCharTerm.length() > 0) {
                    tokens.add(this.expression.substring(start, i));
                }
                // Add operator or parenthesis term to list
                if (c != ' ') {
                    tokens.add(c.toString());
                }
                // Get ready for next term
                start = i + 1;
                multiCharTerm = new StringBuilder();
            } else {
                // multi character terms: numbers, functions, perhaps non-supported elements
                // Add next character to working term
                multiCharTerm.append(c);
            }

        }
        // Add last term
        if (multiCharTerm.length() > 0) {
            tokens.add(this.expression.substring(start));
        }
    }

    private Double Calculate(Double num1, Double num2, String operator){
        Double answer = 0.0;
        switch(operator){ // switch case based on what operation we want to run. 
            case "+":
                answer = num1 + num2;
               break;
            case "-":
                answer =  num1 - num2;
                break;
            case "*":
                answer = num1 * num2;
                break;
            case "/":
                answer = num1/num2;

                break;

            case "^":
                answer = Math.pow(num1, num2);
                break;

            case "%":
                answer = num1 % num2;
                break;

            case "√":
                answer = Math.sqrt(num2);


            default:
                System.out.println("Operator did not work");
                break;
        }
        return answer;
    }

    // Key instance variables
    private final String expression;
    private ArrayList<String> tokens;
    private ArrayList<String> reverse_polish;
    private Double result;

    private Double rpnToResult() {
        Stack<Double> calculation = new Stack<>();
        Double num1 = 0.0,num2 = 0.0; // Initialize the top two numbers in the top of the stack
         for (int i = 0; i < reverse_polish.size(); i++){ // Loop to iterate through the whole array
            String current_Token = reverse_polish.get(i);
            if(isOperator(current_Token) ){ // If the current token is a operator, pop the two nums in the top of the stack.
                num2 = calculation.pop();
                if (!current_Token.equals("√")) { // only need num 2 for sqrt
                  num1   = calculation.pop();
                }
                result = Calculate(num1, num2, current_Token); // Method runs math operations.
                calculation.add(result);
            }
            else{
                calculation.add(Double.valueOf(reverse_polish.get(i)));
            }

        }

        return result;

    }

    // Print the expression, terms, and result
    public String toString() {
        return ("Original expression: " + this.expression + "\n" +
                "Tokenized expression: " + this.tokens.toString() + "\n" +
                "Reverse Polish Notation: " +this.reverse_polish.toString() + "\n" +
                "Final result: " + String.format("%.2f", this.result));
    }





    public static void main(String[] args){
        Calculator simpleMath = new Calculator("100 + 200  * 3");
        System.out.println("Simple Math\n" + simpleMath);

        Calculator parenthesisMath = new Calculator("(100 + 200)  * 3");
        System.out.println("Parenthesis Math\n" + parenthesisMath);

        Calculator allMath = new Calculator("200 % 300 + 5 + 300 / 200 + 1 * 100");
        System.out.println("All Math\n" + allMath);

        Calculator allMath2 = new Calculator("200 % (300 + 5 + 300) / 200 + 1 * 100");
        System.out.println("All Math2\n" + allMath2);

        Calculator exponent = new Calculator("2 ^ 4 + 500"); // Math problem with exponent
        System.out.println("Exponent\n" + exponent);

        Calculator triangle = new Calculator("√((3^2) + (4^2))"); // EC: Math problem with sqrt
        System.out.println("Triangle\n" + triangle);
    }
}


```
```
Output: 

Simple Math
Original expression: 100 + 200  * 3
Tokenized expression: [100, +, 200, *, 3]
Reverse Polish Notation: [100, 200, 3, *, +]
Final result: 700.00
Parenthesis Math
Original expression: (100 + 200)  * 3
Tokenized expression: [(, 100, +, 200, ), *, 3]
Reverse Polish Notation: [100, 200, +, 3, *]
Final result: 900.00
All Math
Original expression: 200 % 300 + 5 + 300 / 200 + 1 * 100
Tokenized expression: [200, %, 300, +, 5, +, 300, /, 200, +, 1, *, 100]
Reverse Polish Notation: [200, 300, %, 5, +, 300, 200, /, +, 1, 100, *, +]
Final result: 306.50
All Math2
Original expression: 200 % (300 + 5 + 300) / 200 + 1 * 100
Tokenized expression: [200, %, (, 300, +, 5, +, 300, ), /, 200, +, 1, *, 100]
Reverse Polish Notation: [200, 300, 5, +, 300, +, %, 200, /, 1, 100, *, +]
Final result: 101.00
Exponent
Original expression: 2 ^ 4 + 500
Tokenized expression: [2, ^, 4, +, 500]
Reverse Polish Notation: [2, 4, ^, 500, +]
Final result: 516.00
Operator did not work
Triangle
Original expression: √((3^2) + (4^2))
Tokenized expression: [√, (, (, 3, ^, 2, ), +, (, 4, ^, 2, ), )]
Reverse Polish Notation: [3, 2, ^, 4, 2, ^, +, √]
Final result: 5.00

```

## Week 1

```java
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
        if (n != null) { // check if head has a node
            n.setPrevNode(null);
            this.head = n;
        }else{
            this.head= this.tail= null; // tail and head become the same on the last iteration
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
        while (this.queue.getHead() != null) { // delete when head has a value
            this.queue.delete();
            this.count--;
            printQueue();   // printing after removal
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
