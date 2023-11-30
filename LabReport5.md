# Lab Report 5 - Putting It All Together

## Step 1

jUnit Test Errors

***

Cesar Lopez: Hello, I was curious why my JUnit test runs into a TimeOutException. Could it be a bug on my jUnit test or the file itself?

![JUnit Failure](https://github.com/Lope879/cse15l-lab-reports/assets/100965607/4a4a4cd0-e5b2-4569-a01c-c0a00ac38428)


1 Answer

***

TA Member: Hello Cesar, the error seems to be found in the file itself. Try scanning the content of the file ListExamples.java using the vim command and
checking the bug found in the class's merge command. When you find the error, you can use insert mode in vim to fix the bug.

Cesar Lopez: I used the vim command on ListExamples.java and found that the third while loop in the command merge does not update its proper variable.
It should be updating variable index2 instead of index1. Since the correct variable isn't being updated, the loop never ends and causes a TimeOutException.

![File Content and Bug](https://github.com/Lope879/cse15l-lab-reports/assets/100965607/209e2159-5f50-4d11-b4a7-ac8dd92d6564)

Cesar Lopez: The information needed for the setup is the following: 
The files I need are ListExamples.java, TestListExamples.java and test.sh as well as hamcrest-core-1.3.jar  junit-4.13.2.jar used for the JUnit tests.
The current directory should contain these files while the hamcrest-core-1.3.jar and junit-4.13.2.jar files are found in a folder called lib.
The contents of each file before fixing the bug go as follows:

test.sh

```
set -e

javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java

java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore TestListExamples
```

TestListExamples.java

```
import java.util.ArrayList;
import java.util.List;
import java.util.Arrays;
import static org.junit.Assert.*;
import org.junit.*;

public class TestListExamples {
  @Test
  public void testFilter() {
    List<String> strs = new ArrayList<>();
    strs.add("a");
    strs.add("b");
    strs.add("apple");
    List<String> filtered = ListExamples.filter(strs, s -> s.charAt(0) == 'a');
    assertEquals(filtered, Arrays.asList("a", "apple"));
  }
  
  @Test(timeout=100)
  public void testMerge() {
    List<String> strs1 = new ArrayList<>();
    List<String> strs2 = new ArrayList<>();
    strs1.add("a"); strs1.add("b"); strs1.add("cranberry");
    strs2.add("dragon");
    List<String> merged = ListExamples.merge(strs1, strs2);
    assertEquals(merged, Arrays.asList("a", "b", "cranberry", "dragon"));
  }
}
```

ListExamples.java

```
import java.util.ArrayList;
import java.util.List;

interface StringChecker { boolean checkString(String s); }

class ListExamples {

  // Returns a new list that has all the elements of the input list for which
  // the StringChecker returns true, and not the elements that return false, in
  // the same order they appeared in the input list;
  static List<String> filter(List<String> list, StringChecker sc) {
    List<String> result = new ArrayList<>();
    for(String s: list) {
      if(sc.checkString(s)) {
        result.add(s);
      }
    }
    return result;
  }


  // Takes two sorted list of strings (so "a" appears before "b" and so on),
  // and return a new list that has all the strings in both list in sorted order.
  static List<String> merge(List<String> list1, List<String> list2) {
    List<String> result = new ArrayList<>();
    int index1 = 0, index2 = 0;
    while(index1 < list1.size() && index2 < list2.size()) {
      if(list1.get(index1).compareTo(list2.get(index2)) < 0) {
        result.add(list1.get(index1));
        index1 += 1;
      }
      else {
        result.add(list2.get(index2));
        index2 += 1;
      }
    }
    while(index1 < list1.size()) {
      result.add(list1.get(index1));
      index1 += 1;
    }
    while(index2 < list2.size()) {
      result.add(list2.get(index2));
      index1 += 1;
    }
    return result;
  }
}
```

I triggered the bug by running `bash test.sh`. The line that causes the error is in TestListExamples.java `List<String> merged = ListExamples.merge(strs1, strs2);` 
since it runs the merge command in ListExamples.java.

To fix the bug, edit the third while loop in ListExamples.java so that the variable being updated is not `index1 += 1` but `index2 += 1`.


## Step 2 

Some things I learned from lab in the second half of the quarter has been how to make and edit directories and files from the terminal such as by using commands `mkdir`, `touch`, and `vim`. 
I have learned what bash scripts are and how to make one and run one. Something cool I also learned was how to run files with jdb, the java debugger, in order to inspect the variables in certain lines of code
and be able to inspect the code before it completely ends.
