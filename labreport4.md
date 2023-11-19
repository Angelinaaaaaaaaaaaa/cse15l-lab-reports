# Lab Report 3

## Step 4
Log into your ieng6 account: simply type `ssh cs15lfa23ab@ieng6.ucsd.edu`, but replace "ab" with your account number.

![image](https://github.com/Angelinaaaaaaaaaaaa/cse15l-lab-reports/assets/115201846/bacbfc97-0a4a-4dc7-b7bb-8644ccdee9ab)


## Step 5
To clone the repository you just forked, type `git clone git@github.com:<GitHub username>/lab7.git` in the terminal.

![image](https://github.com/Angelinaaaaaaaaaaaa/cse15l-lab-reports/assets/115201846/92bda6c6-1a2a-49d6-ae83-9318de7468e9)


## Step 6
Next, we should enter the directory we cloned from GitHub by typing `cd lab7`. To run the JUnit tests, we need first to run `javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java` to compile the program and then type `java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests` to run the code.
We can also use `bash test.sh` instead.

![image](https://github.com/Angelinaaaaaaaaaaaa/cse15l-lab-reports/assets/115201846/ddd755fb-1017-4817-8b77-2cc143585d3a)


## Step 7

To fix the code, I typed `vim TestExamples.java`. Inside the vim tool, I first pressed `/index1` to find the place of the error. Then, I use `i` to change into the insert mode so that I can insert (or change) some content of this file. Then, I navigated to the fourth-til-last row, and fix the error by changing 1 into 2.

![image](https://github.com/Angelinaaaaaaaaaaaa/cse15l-lab-reports/assets/115201846/6a93527d-2f3a-4590-9340-92d70001c9e0)

![image](https://github.com/Angelinaaaaaaaaaaaa/cse15l-lab-reports/assets/115201846/f88bcda8-6891-4361-9569-e5655bccf986)


## Step 8
Next, to rerun the tests, we need to repeat what we did in Step 6 again.
![image](https://github.com/Angelinaaaaaaaaaaaa/cse15l-lab-reports/assets/115201846/ae3da54b-1b79-4d76-8518-aab6d6e16b9e)


## Step 9
To push the code to our GitHub repository, we should first type `git add ListExamples.java`. Next, type `git commit -m "your_message"` to commit the code to git. Lastly, type `git push` to push the changes to the origin. 
![image](https://github.com/Angelinaaaaaaaaaaaa/cse15l-lab-reports/assets/115201846/d6fe766b-234c-486b-bd53-ad1acd714441)

![image](https://github.com/Angelinaaaaaaaaaaaa/cse15l-lab-reports/assets/115201846/725f8e2e-9d92-4093-828b-bafaad440d28)




## Step 8
