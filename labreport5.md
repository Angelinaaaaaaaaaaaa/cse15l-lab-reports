# Lab Report 5

### Part 1 - Debugging Scenario

#### Student: 
Hi, I'm trying to run JUnit tests in my bash script, but it's not detecting any test cases. I have three tests in my testing file, and I expected to see JUnit run through all three tests and pass them. It seems like the tests are not being recognized. I guess it is because of the file structure. Could you tell me what might be causing this issue?
![image](https://github.com/Angelinaaaaaaaaaaaa/cse15l-lab-reports/assets/115201846/d285554a-3e52-4bb7-a239-2674d3383840)

#### TA:
Hi! The issue here is with the classpath separator, and your file structure is correct. On Windows, the classpath separator is `;`, and on Unix-like systems (Mac), it's `:`. In your CPATH variable, you are using an incorrect separator for your Windows system.
Let's correct the script for your Git Bash environment with the commands: 
```
CPATH='.;lib/hamcrest-core-1.3.jar;lib/junit-4.13.2.jar'

javac -cp "$CPATH" *.java
java -cp "$CPATH" org.junit.runner.JUnitCore ArrayTests
```

#### Student:
Thank you for the help! The corrected script indeed runs the tests. However, it seems I failed one test. Here's the updated screenshot:
![image](https://github.com/Angelinaaaaaaaaaaaa/cse15l-lab-reports/assets/115201846/3891fc96-6d0f-4d90-b8da-dbcba31ff0b0)
This is my code for each file:
ArrayTests.java
```
import static org.junit.Assert.*;
import org.junit.*;
import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;


public class ArrayTests {
	@Test 
	public void testReverseInPlace() {
    int[] input1 = { 3 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 3 }, input1);
	}


  @Test
  public void testReversed() {
    int[] input1 = { };
    assertArrayEquals(new int[]{ }, ArrayExamples.reversed(input1));
  }
  
  @Test 
  public void testReversed2() {
    int[] input = {1, 2, 3};
    int[] result = ArrayExamples.reversed(input);
    assertArrayEquals(new int[]{3, 2, 1}, result);
  }

  @Test 
  public void testReverseInPlace2() {
    int[] input = {2};
    ArrayExamples.reverseInPlace(input);
    assertArrayEquals(new int[]{2}, input);
  }
}
```

ArrayExamples.java
```
public class ArrayExamples {

  // Changes the input array to be in reversed order
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < (arr.length/2); i += 1) {
      int temp = arr[i];
      arr[i] = arr[arr.length - i - 1];
      arr[arr.length - i - 1] = temp;
    }
  }


  // Returns a *new* array with all the elements of the input array in reversed
  // order
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }

  // Averages the numbers in the array (takes the mean), but leaves out the
  // lowest number when calculating. Returns 0 if there are no elements or just
  // 1 element in the array
  static double averageWithoutLowest(double[] arr) {
    if(arr.length < 2) { return 0.0; }
    double lowest = arr[0];
    for(double num: arr) {
      if(num < lowest) { lowest = num; }
    }
    double sum = 0;
    for(double num: arr) {
      if(num != lowest) { sum += num; }
    }
    return sum / (arr.length - 1);
  }

}
```
I think it is because of the reversed method, which was supposed to reverse the input list. However, the elements remained unchanged after I applied the method to the input list. 

Can you give me some hints, please?

#### TA:
It looks like the failure is happening in the testReversed2 method of your ArrayTests class. Let's take a closer look at the reversed method in your ArrayExamples class and see if we can identify the problem.
```
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }
```

Here, you are modifying the original array arr instead of populating the new array newArray. 

#### Student:
Oh! I should be assigning values from arr to newArray. Let me fix that and run the tests again.
```
static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for (int i = 0; i < arr.length; i += 1) {
        newArray[i] = arr[arr.length - i - 1];
    }
    return newArray;
}
```


![image](https://github.com/Angelinaaaaaaaaaaaa/cse15l-lab-reports/assets/115201846/8430d9f4-acab-4caa-9c68-39a700cd5799)
Yes, the test passed now. Thank you for your help!

#### TA:
You are welcome!

Step 4. All the necessary information was incorporated into the conversation above.

### Part 2 - Reflection

During the second half of this quarter, I gained a deeper understanding of Vim and jdb, both of which were new tools for me. Learning to navigate and edit text efficiently using Vim's modal interface was initially challenging but immensely rewarding in terms of increased productivity. Additionally, using jdb for debugging provided insights into the internal workings of Java programs, allowing me to diagnose and fix issues more effectively by examining the program's state at various points in execution.
