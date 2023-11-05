# Lab Report 3

## Part1 Bugs
### A failure-inducing input for the buggy program, as a JUnit test and any associated code (write it as a code block in Markdown)
```
  @Test 
  public void testReverseInPlace1() {
    int[] input = {1, 2, 3};
    ArrayExamples.reverseInPlace(input);
    assertArrayEquals(new int[]{3, 2, 1}, input);
  }

JUnit version 4.13.2
.E..
Time: 0.012
There was 1 failure:
1) testReverseInPlace1(ArrayTests)
arrays first differed at element [2]; expected:<1> but was:<3>
        at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:78)
        at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:28)
        at org.junit.Assert.internalArrayEquals(Assert.java:534)
        at org.junit.Assert.assertArrayEquals(Assert.java:418)
        at org.junit.Assert.assertArrayEquals(Assert.java:429)
        at ArrayTests.testReverseInPlace1(ArrayTests.java:36)
        ... 32 trimmed
Caused by: java.lang.AssertionError: expected:<1> but was:<3>
        at org.junit.Assert.fail(Assert.java:89)
        at org.junit.Assert.failNotEquals(Assert.java:835)
        at org.junit.Assert.assertEquals(Assert.java:120)
        at org.junit.Assert.assertEquals(Assert.java:146)
        at org.junit.internal.ExactComparisonCriteria.assertElementsEqual(ExactComparisonCriteria.java:8)
        at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:76)
        ... 38 more

FAILURES!!!
Tests run: 3,  Failures: 1
```

### An input that doesn’t induce a failure, as a JUnit test and any associated code (write it as a code block in Markdown)
```
  @Test 
  public void testReverseInPlace2() {
    int[] input = {2};
    ArrayExamples.reverseInPlace(input);
    assertArrayEquals(new int[]{2}, input);
  }
}

JUnit version 4.13.2
.
Time: 0.008

OK (1 test)
```

### The symptom, as the output of running the tests (provide it as a screenshot of running JUnit with at least the two inputs above)

![image](https://github.com/Angelinaaaaaaaaaaaa/cse15l-lab-reports/assets/115201846/929c3ca7-a50b-424d-ab1e-6f5a26c721d9)

### The bug, as the before-and-after code change required to fix it (as two code blocks in Markdown)
Before:
```
static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
```

After:
```
static void reverseInPlace(int[] arr) {
    for(int i = 0; i < (arr.length/2); i += 1) {
      int temp = arr[i];
      arr[i] = arr[arr.length - i - 1];
      arr[arr.length - i - 1] = temp;
    }
  }
```
The original code attempted to reverse an array `arr` in place, but it had a critical flaw. It iterated through the entire array, and at each step, it replaced the current element with the element at the corresponding position counting from the end of the array. While this approach might seem logical, it led to an unintended behavior. After reversing the first half of the array, the code continued swapping elements, causing the second half of the array to overwrite the reversed elements, resulting in a symmetric but incorrect array.

To fix this issue, instead of attempting to reverse the entire array by iterating through it from start to end, I make the code only reverses the first half of the array, which is key to ensuring that we don't re-reverse the already reversed elements during the second half of the iteration. The revised code iterates through the array up to its midpoint (i.e., `arr.length/2`). During this iteration, it swaps the elements between the first half and the second half, effectively reversing the order. To achieve this, a temporary variable `temp` is used to store the value of the element at the current position before performing the swap. This ensures that the reversed elements are preserved, and the array is correctly reversed from start to finish.

By making these modifications, we prevent the erroneous symmetrical reversal of the array and correctly reverse it. The revised code maintains the integrity of the elements and produces the expected result—a completely reversed array.

In summary, the key improvement in the revised code is the introduction of a loop that only iterates through the first half of the array, along with the use of a temporary variable to facilitate the swap, ensuring a correct in-place reversal without symmetric distortions.
  
