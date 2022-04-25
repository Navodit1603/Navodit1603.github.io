# 2015 AP Exam Practice Test Corrections

## MC
### Score: 24/39



<details>
<summary>Question 26</summary>
<br>
- Method does not change nums or the string
   <br>
- The method is the same in the main start method.
   <br>
- Original array will be printed and the original string will be printed.
</details>


<details>
<summary>Question 27</summary>
<br>
* Two for loops for sorting algorithm
   <br>
* Keep track of variables on paper
   <br>
* Moves number in the back to front
</details>


<details>
<summary>Question 28</summary>
<br>
* It is easy to see that the outer for loop will run 5 times.
   <br>
* The j value is not changed outside of the for loop statement.
   <br>
* The array has a length of 5. 
   <br>
* The inner loop iterates one less time every j value.
   <br>
* 5 + 4 + 3 + 2 + 1 = 15
   <br>
* Answer: 15/5
</details>

<details>
<summary>Question 29</summary>
<br>
* The code determines the amount of digits in yor integer.
   <br>
* If the number is less than ten, it returns one, which means one integer
   <br>
* Otherwise, it goes into the function until one is returned.
   <br>
* It adds up all the 1s that were returned before. 
   <br>
Giving the number of time the number was divided by ten.
</details>

<details>
<summary>Question 30</summary>
<br>
* I does not work because if the customer buys more than 0 boxes, it would always print the maximum value.
   This can be fixed by putting an if else.
   <br>
* II does works because it checks for the greatest number correctly and uses if else so the cost is only changed once. 
   <br>
* III does not work because if the cost is more than 5 or 10, the code will still end on the first statement.  
</details>

<details>
<summary>Question 31</summary>
<br>
* Double array is initialized
   <br>
* Follow through the for loop
   <br>
* For ease, write down values as they change
   <br>
* Keep a sketch of the board
   <br>
* x is place diagonally after skipping one diagonal line.
</details>

<details>
<summary>Question 32</summary>
<br>
* The user inputs a major into the parameters
   <br>
* Then with a for each loop, the code iterates through each student.
   <br>
* They identify the student's major through the major getter method.
   <br>
* With the getAge method, the age is added to the sum and the count has been increased.
   <br>
* Sum and count then are used for the average
   <br>
* Wrong answers include getting age and major without a getter
   <br>
* Other wrong answers use array lists when not needed
   <br>
</details>

<details>
<summary>Question 33</summary>
<br>
* I. works because it sets the minimum integer value to the maximum and changes it when it finds a bigger value.
   <br>
* II. Boolean set to true and then set to false after first if statement. 
If statement was used for assigning the first value in the array to the max.
Then, the code iterates through every element to find a bigger number.
   <br>
* III. Sets first value of the array as max. Iterates though every element to find the max.
   <br>
* All three work
</details>

<details>
<summary>Question 34</summary>
<br>
* Size of an array list has to be found by lostOfWords.size()
   <br>
* Don't need -1 at the end.
   <br>
* Condition: If we are not at the end of the list, add a comma
   <br>
* Else, finish the code by adding a "}"
   <br>
</details>

<details>
<summary>Question 35</summary>
<br>
* Dataset cut into half to find the target number
   <br>
* If number is greater than mid, first half is ignored
   <br>
* Start value gets moved to mid + 1
   <br>
* Process starts again until target is found
   <br>
</details>

<details>
<summary>Question 36</summary>
<br>
* As the loop iterates, the size is divided into two
   <br>
* In order to reach 1, we have to half the array 11 times.
</details>

<details>
<summary>Question 37</summary>
<br>
* II works because it starts from the end and the counter goes back.
With it, the words can be printed in reverse order upto the index in the parameter.
   <br>
* III works because it moves items in the front to the back.
</details>

<details>
<summary>Question 38</summary>
<br>
* Returns the number of elements in numbers that are equal to val
   <br>
* If statement adds one if the previous number is the same
   <br>
* Recursive method. 
</details>

<details>
<summary>Question 39</summary>
<br>
* The first for loop prints all the elements before switching them.
   <br>
* The second for loop also prints out each element but all of them have been changed to Alex.
</details>

## FRQ

* [FRQ](https://drive.google.com/file/d/1gWqgAsqmUE9M-JYlVYFrVV1W5nNlHMdl/view?usp=sharing)
* [Repl]()

<details>
<summary>Question 1</summary>
<br>

```java
    public static int arraySum(int[] arr){
        int sum = 0;
        for(int i = 0; i < arr.length; i++){
            sum += arr[i];
        }
        return sum;
    }

    public static int[] rowSum(int[][] arr2D){
        int[] arr = new int[arr2D.length];
        for(int i = 0; i < arr2D.length; i++){
            arr[i] = arraySum(arr2D[i]);
        }
        for(int i = 0; i < arr.length; i++){
        }
        return arr;
    }

    public static boolean isDiverse(int[][] arr2D){
        int[] sums = rowSum(arr2D);
        for(int i = 0; i < sums.length; i++){
            for(int j = i + 1; j< sums.length; j++){
                if(sums[i] == sums[j]){
                    return false;
                }
            }
        }
        return true;
    }

    public static void main(String[] args){
        int[] arr = {2, 3, 5, 6, 4, 1};
        int[][] arr2D = {{1, 1, 5, 3, 4}, {12, 7, 6, 1, 9}, {8, 11, 10, 2, 5}, {3, 2, 3, 0, 6}};

        int sum = arraySum(arr);
        System.out.println("Sum");
        System.out.println(sum);
        System.out.println("");

        int[] array = rowSum(arr2D).clone();
        System.out.println("Array");
        for(int i = 0; i < array.length; i++){
            System.out.print(array[i] + " ");
        }
        System.out.println("");
        System.out.println("");

        Boolean diverse = isDiverse(arr2D);
        System.out.println("Boolean");
        System.out.println(diverse);
        System.out.println("");
    }
```
</details>

<details>
<summary>Question 2</summary>
<br>

```
    public String word;

    public HiddenWord(String m_word){
        word = m_word;
    }

    public String getHint(String guess){
        String hint = "";
        for(int i = 0; i < guess.length(); i++){
            if(guess.substring(i, i+1).equals(word.substring(i,i+1))){
                hint += guess.substring(i, i+1);
            }
            else if(word.contains(guess.substring(i, i + 1))){
                hint += "+";
            }
            else {
                hint += "*";
            }
        }
        return hint;
    }

    public static void main(String[] args){
        HiddenWord hint = new HiddenWord("navodit");
        System.out.println("Type in a word: ");
        for(int i = 0; i < 4; i++) {
            Scanner scan = new Scanner(System.in);
            String guess = scan.nextLine();
            String result = hint.getHint(guess);
            System.out.println(result);
            if(guess.equals(result)){
                break;
            }
        }
    }
```

</details>


<details>
<summary>Question 3</summary>
<br>

```java
public class SparseArrayEntry {

    // row and column index for this entry in the sparse array
    private int row;
    private int col;

    // the value of this entry in the sparse array
    private int value;

    public SparseArrayEntry(int r, int c, int v){
        row = r;
        col = c;
        value = v;
    }

    public int getRow(){
        return row;
    }

    public int getCol(){
        return col;
    }

    public int getValue(){
        return value;
    }


}


```

</details>

<details>
<summary>Question 4</summary>
<br>

```java
public interface NumberGroup {
    boolean contains(int i);
}
```
```java
public class Range implements NumberGroup {
    private int min;
    private int max;

    public Range(int min, int max) {
        this.min = min;
        this.max = max;
    }

    @Override
    public boolean contains(int i) {
        return this.min <= i && i <= this.max;
    }
}
```
```java
import java.util.Arrays;
import java.util.List;

public class MultipleGroups implements NumberGroup { 
    private List<NumberGroup> groupList;

    public MultipleGroups(NumberGroup... groups) {
        this.groupList = Arrays.asList(groups);
    }

    @Override
    public boolean contains(int i) {
        for (NumberGroup group : groupList)
            if (group.contains(i))
                return true;
        return false;
    }
}
```

</details>
