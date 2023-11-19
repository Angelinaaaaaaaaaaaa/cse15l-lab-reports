# Lab Report 3

## Part 1 - Bugs
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
![image](https://github.com/Angelinaaaaaaaaaaaa/cse15l-lab-reports/assets/115201846/3fba4069-c69e-4269-b83b-d3e47e2de0c7)


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


## Part 2 - Researching Commands

I choose `grep` command, and  I used online search on https://www.geeksforgeeks.org/grep-command-in-unixlinux/ and combined the command on the files we used in lab.

### Option 1: -i (Ignore case)
The -i option is used to perform a case-insensitive search. It allows grep to match patterns regardless of the letter casing, making it useful when you want to find matches regardless of whether they are in uppercase or lowercase.
```
Angelina Zhang@AngelinaZ MINGW64 ~/Desktop/cse15l/docsearch (main)
$ grep -i "LEGAL" technical/government/Media/*.txt
technical/government/Media/5_Legal_Groups.txt:5 Legal Groups at 1 Locale To Serve the February 3, 2002
technical/government/Media/5_Legal_Groups.txt:Five independent Salt Lake organizations that provide legal
technical/government/Media/5_Legal_Groups.txt:Legal Center at 205 N. 400 West is a project of "And Justice for
technical/government/Media/5_Legal_Groups.txt:campaign by an alliance of the non-profit providers of free legal
technical/government/Media/5_Legal_Groups.txt:campaign of legal services agencies in the country, and the
technical/government/Media/5_Legal_Groups.txt:Community Legal Center is the first joint office project of public
technical/government/Media/5_Legal_Groups.txt:The Legal Aid Society of Salt Lake, the Disability Law Center,
technical/government/Media/5_Legal_Groups.txt:the Multi-Cultural Legal Center, the Senior Lawyer Volunteer
...
```

```
Angelina Zhang@AngelinaZ MINGW64 ~/Desktop/cse15l/docsearch (main)
$ grep -i "LEGAL" technical/911report/*.txt
technical/911report/chapter-1.txt:    Passengers on three flights reported the hijackers' claim of having a bomb. The FBI told us they found no trace of explosives at the crash sites. One of the passengers who mentioned a bomb expressed his belief that it was not real. Lacking any evidence that the hijackers attempted to smuggle such illegal items past the security screening checkpoints, we believe the bombs were probably fake.
technical/911report/chapter-10.txt:            In addition, Bush and his advisers discussed new legal authorities for covert action
technical/911report/chapter-11.txt:                initiative, in the legal issues that would be involved in shooting down a U.S.
technical/911report/chapter-11.txt:                plot. Information was not shared, sometimes inadvertently or because of legal
technical/911report/chapter-12.txt:            While efforts to shut down Libya's illegal nuclear program have been generally
technical/911report/chapter-12.txt:                laws and an international legal regime with universal jurisdiction to enable the
technical/911report/chapter-12.txt:                actions appeared to have little effect and, when confronted by legal challenges, the
technical/911report/chapter-12.txt:            More than 500 million people annually cross U.S. borders at legal entry points, about
technical/911report/chapter-12.txt:                330 million of them noncitizens. Another 500,000 or more enter illegally without
technical/911report/chapter-12.txt:                investigation as to their source, or legal process.
technical/911report/chapter-12.txt:                    transit passage areas can be fully secured to prevent passengers from illegally
technical/911report/chapter-12.txt:                outside the legal immigration system. We must also be able to monitor and respond to
technical/911report/chapter-12.txt:                    company to its employees and the public for legal purposes. Private-sector
technical/911report/chapter-13.1.txt:                many stoves that are legally and politically entitled to have cast-iron pipes of
...
```
For instance, as I search for 'LEGAL' in Media folder and 911report folder, all txt files with the word legal in them are found.

### Option 2: Recursive Search (-r)
The -r (or --recursive) option is used for recursive searching. When this option is specified, grep searches not only in the specified directory but also in all subdirectories. It's handy for searching for patterns across an entire directory tree.

```
Angelina Zhang@AngelinaZ MINGW64 ~/Desktop/cse15l/docsearch (main)
$ grep -r "unsupported" technical/
technical/biomed/1471-2148-2-17.txt:          probability as estimated by MrBayes and unsupported as
technical/biomed/1471-2148-2-17.txt:          unsupported within a
technical/biomed/1471-2148-2-17.txt:          for this subclade is unsupported by the ITS data.
technical/government/Gen_Account_Office/d0269g.txt:duplicate payments and miscalculations; payments for unsupported or
technical/government/Gen_Account_Office/d02701.txt:process risk becoming unsupported by critical knowledge. In leading
technical/government/Gen_Account_Office/Letter_Walkeraug17let.txt:to statutes and excludes the Constitution is unsupported. As we
```

```
Angelina Zhang@AngelinaZ MINGW64 ~/Desktop/cse15l/docsearch (main)
$ grep -r "unsupported" technical/biomed/
technical/biomed/1471-2148-2-17.txt:          probability as estimated by MrBayes and unsupported as
technical/biomed/1471-2148-2-17.txt:          unsupported within a
technical/biomed/1471-2148-2-17.txt:          for this subclade is unsupported by the ITS data.
```
For instance, I searched for the word unsupported in two folders, and the `-r` let it recursively search for this word in all files in the directory and subdirectories.

### Option 3: -w (word-regexp)

This option tells grep to match whole words only, ensuring that the pattern is surrounded by non-word characters (such as spaces, punctuation, etc.) and it's used when you want to search for a pattern as a complete word and not as a substring within other words.

```
Angelina Zhang@AngelinaZ MINGW64 ~/Desktop/cse15l/docsearch (main)
$ grep -w "LEGAL" technical/911report/*.txt
```
```
Angelina Zhang@AngelinaZ MINGW64 ~/Desktop/cse15l/docsearch (main)
$ grep -w "legal" technical/911report/*.txt
technical/911report/chapter-10.txt:            In addition, Bush and his advisers discussed new legal authorities for covert action
technical/911report/chapter-11.txt:                initiative, in the legal issues that would be involved in shooting down a U.S.
technical/911report/chapter-11.txt:                plot. Information was not shared, sometimes inadvertently or because of legal
technical/911report/chapter-12.txt:                laws and an international legal regime with universal jurisdiction to enable the
technical/911report/chapter-12.txt:                actions appeared to have little effect and, when confronted by legal challenges, the
technical/911report/chapter-12.txt:            More than 500 million people annually cross U.S. borders at legal entry points, about
technical/911report/chapter-12.txt:                investigation as to their source, or legal process.
technical/911report/chapter-12.txt:                outside the legal immigration system. We must also be able to monitor and respond to
technical/911report/chapter-12.txt:                    company to its employees and the public for legal purposes. Private-sector
technical/911report/chapter-13.1.txt:                    responsibility and necessary legal authorities in one entity.
technical/911report/chapter-13.1.txt:                    revolution. He should coordinate the resolution of the legal, policy, and
technical/911report/chapter-13.1.txt:                White House leadership is also needed because the policy and legal issues are
technical/911report/chapter-13.1.txt:                    were outside of the Department of Justice, the process of legal oversight-never
technical/911report/chapter-13.1.txt:                    and 47 legal attach� offices; a laboratory, operations center, and training
technical/911report/chapter-13.4.txt:                investigations. Moreover, the legal bar to sharing information was often
technical/911report/chapter-13.4.txt:                the existing legal authorities for covert action against Bin Ladin were unclear and
technical/911report/chapter-13.4.txt:            71. Atta was admitted as a tourist for an eight-month stay, even though the legal
technical/911report/chapter-13.5.txt:                from the legal limits we discussed in section 3.2. The Attorney General's July 1995
technical/911report/chapter-13.5.txt:                introduction to these legal limits and "the wall," see section 3.2. In December
technical/911report/chapter-13.5.txt:                caveats and legal barriers to information sharing and rules governing criminal
technical/911report/chapter-13.5.txt:            Simply put, there was no legal reason why the information the analyst possessed could
technical/911report/chapter-13.5.txt:            31. For legal entry, see White House report, Office of Homeland Security, "The
technical/911report/chapter-3.txt:            Third, the successful use of the legal system to address the first World Trade Center
technical/911report/chapter-3.txt:                the CIA and from Army Intelligence. The legal basis for some of this assistance was
technical/911report/chapter-3.txt:            Freeh recognized terrorism as a major threat. He increased the number of legal
technical/911report/chapter-3.txt:                officials. He pressed for more cooperation between legal attach�s and CIA stations
technical/911report/chapter-3.txt:            There were other legal limitations. Both prosecutors and FBI agents argued that they
technical/911report/chapter-3.txt:                lives outside the legal framework. Fraudulent documents could be easily obtained.
technical/911report/chapter-3.txt:                that the legal basis and presidential authorization for their actions were
technical/911report/chapter-3.txt:                Bin Ladin. Ambassador Carney had no legal basis to ask for more from the Sudanese
technical/911report/chapter-3.txt:                the CIA planners to go ahead and, among other things, start drafting any legal
technical/911report/chapter-3.txt:            On May 18, CIA's managers reviewed a draft Memorandum of Notification (MON), a legal
technical/911report/chapter-3.txt:                the Attorney General gave sufficient legal authority for domestic investigation and
technical/911report/chapter-3.txt:                NSC's legal adviser to inform Albright, Cohen, Shelton, and Reno. None was allowed
technical/911report/chapter-3.txt:                any legal objection. A copy of the final document, along with the carefully crafted
technical/911report/chapter-3.txt:            Later in 1999, when legal authority was needed for enlisting still other
technical/911report/chapter-3.txt:            The dispute turned out to be somewhat academic, as the limits of available legal
technical/911report/chapter-6.txt:                taking legal action to prevent terrorists from coming into the United States
technical/911report/chapter-6.txt:                completed and the equipment was ready, but legal issues were still being ironed
technical/911report/chapter-6.txt:                legal standard. Because the attack was the subject of a criminal investigation, they
technical/911report/chapter-6.txt:                terrorism. Election night became a 36-day legal fight. Until the Supreme Court's 5-4
technical/911report/chapter-6.txt:            During the spring, the CIA, at the NSC's request, had developed draft legal
technical/911report/chapter-6.txt:                deciding on a policy before deciding on the legal authorities to implement it.
technical/911report/chapter-6.txt:                concluded that it was legal for the CIA to kill Bin Ladin or one of his deputies
technical/911report/chapter-6.txt:            That same day, Hadley instructed DCI Tenet to have the CIA prepare new draft legal
technical/911report/chapter-7.txt:                status, as Suqami's legal stay in the United States ended May 21.
technical/911report/chapter-8.txt:            The FBI agent's August 18 message requested assistance from the FBI legal attach� in
technical/911report/chapter-8.txt:                from the legal attach� there as well. By August 24, the Minneapolis agent had also
technical/911report/chapter-8.txt:            The FBI legal attach�'s office in Paris first contacted the French government on
technical/911report/chapter-8.txt:            After receiving the written request for assistance, the legal attach� in London had
```
For instance, when I searched for LEGAL in every txt files under the folder 911report, there is no results. However, if I search for the lower case legal, there are multiple results, which validate the case we tried for -i.

### Option 4: -L (files-without-match)

This option instructs grep to list the names of files and suppresses normal output, which helps to quickly identify files contain words.

```
Angelina Zhang@AngelinaZ MINGW64 ~/Desktop/cse15l/docsearch (main)
$ grep -l "legal" technical/911report/*.txt
technical/911report/chapter-1.txt
technical/911report/chapter-10.txt
technical/911report/chapter-11.txt
technical/911report/chapter-12.txt
technical/911report/chapter-13.1.txt
technical/911report/chapter-13.3.txt
technical/911report/chapter-13.4.txt
technical/911report/chapter-13.5.txt
technical/911report/chapter-3.txt
technical/911report/chapter-6.txt
technical/911report/chapter-7.txt
technical/911report/chapter-8.txt
```

```
Angelina Zhang@AngelinaZ MINGW64 ~/Desktop/cse15l/docsearch (main)
$ grep -l "LEGAL" technical/911report/*.txt
```

```
Angelina Zhang@AngelinaZ MINGW64 ~/Desktop/cse15l/docsearch (main)
$ grep -l "unsupported" technical/biomed/*.txt
technical/biomed/1471-2148-2-17.txt
```

For instance, when I searched again for the lower case legal, there are multiple results and each file only appears once without showing every lines with the word in it. Also, the unsupported word only appears in one txt file, which is the same as past example suggests.








