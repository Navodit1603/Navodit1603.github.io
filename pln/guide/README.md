# Study Guide

## Multi Dimensional Array 
* ```
  Two dimensional array:
    int[][] twoD_arr = new int[10][20];
  ```

* ```
  Three dimensional array:
    int[][][] threeD_arr = new int[10][20][30];
  ```
  
* The total number of elements that can be stored in a multidimensional array can be calculated by multiplying the size of all the dimensions.
* ```
  int[][] arr2D = {{1, 1, 5, 3, 4}, {12, 7, 6, 1, 9}, {8, 11, 10, 2, 5}, {3, 2, 3, 0, 6}};
   public static int[] rowSum(int[][] arr2D){
        int[] arr = new int[arr2D.length];
        for(int i = 0; i < arr2D.length; i++){
            arr[i] = arraySum(arr2D[i]);
        }
        for(int i = 0; i < arr.length; i++){
        }
        return arr;
    }

## Substring
* This method has two variants and returns a new string that is a substring of this string. The substring begins with the character at the specified index and extends to the end of this string. And index of substring starts from 1 and not from 0.
* ```
    String str = new String("navodit");
    System.out.println(str.substring(3));
    System.out.println(str.substring(3, 5));
  ```
  ```
  Output:
  odit
  od
  ```
  

## Interface
* In Java, an interface is an abstract type that contains a collection of methods and constant variables. It is one of the core concepts in Java and is used to achieve abstraction, polymorphism and multiple inheritances.
  * ```java
    public interface Electronic {

      // Constant variable
      String LED = "LED";

      // Abstract method
      int getElectricityUse();

      // Static method
      static boolean isEnergyEfficient(String electtronicType) {
          if (electtronicType.equals(LED)) {
              return true;
          }
          return false;
      }

      //Default method
      default void printDescription() {
          System.out.println("Electronic Description");
      }
     }
 
## Implements
* The implements' keyword is useful to implement the interfaces in classes.
* We know that an interface in Java is defined as a special type of class that only contains abstract methods inside it.
* Methods just provides a plan, contract, or a prototype that the classes must follow.
* ```java
  package com.techvidvan.implementskeyword;
  //Defining the Shape interface
  interface Shape {
  //declaring an abstract method of the interface
  public double getArea();
  }
  //class implements the Shape interface using the implements keyword
  class Circle implements Shape {
  public double radius = 5;
  public double getArea() {
  return 3.142 * radius * radius;
  }
  }
  class Rectangle implements Shape {
      public double length = 5;
      public double breadth = 10;
      //providing implementation to the interface methods

  public double getArea() {
  return length * breadth;
  }
  }

  public class Demo {
  public static void main(String args[]) {
  Circle c = new Circle();
  double circleArea = c.getArea();
  System.out.println("Area of Circle is: " + circleArea);
  Rectangle r = new Rectangle();
  double rectangleArea = r.getArea();
  System.out.println("Area of Rectangle is: " + rectangleArea);
       }
    }
```
Output:
Area of Circle is: 78.55
Area of Rectangle is: 50.0
```