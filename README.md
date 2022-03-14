# Navodit's GitHub Homepage


## Week One

https://replit.com/@Navoditmah/menu


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


## Team Project 

[Team Project Plan](https://github.com/Archkitten/m221-nitro-code/wiki/Teams,-Plans,-Jobs#nitro-coder)

| Issues  |  Commits |
| ------------- | ------------- |
| Content Cell  | Content Cell  |
| Content Cell  | Content Cell  |

## AP Test Prep Plan
* Go through all CB Units
* Do practice code problems
* Review Important vocabulary from college board.

## Tech Talk 1
* A data structure is a method of organizing data.
* There are many algorithms for different purposes and they interact with different data structures. Think of algorithms as dynamic underlying pieces that interact with data structures.
* Data Structures and Algorithms can be written using different paradigms.
* An imperative program consists of commands for the computer to perform to achieve a result. Imperative programming focuses on describing "how" a program code works.
* Object Oriented programming (OOP) is a programming paradigm that relies on the concept of classes and objects.
