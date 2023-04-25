
# Part 1

**Code:**
4
​
```
import java.io.IOException;
6
import java.net.URI;
7
​
8
class AddMessages implements URLHandler {
9
​
10
    String s1 = "";
11
​
12
    public String addMessage(URI url) {
13
​
14
        if (url.getPath().equals("/add-message")) {
15
​
16
            String[] parameters = url.getQuery().split("=");
17
​
18
                s1 = s1 + parameters[1] + "\n";
19
​
20
                return s1;
21
        }
22
​
23
        return "Add a message!";
24
    }
25
}
26
​
27
class StringServer {
28
    public static void main(String[] args) throws IOException {
29
        if(args.length == 0){
30
            System.out.println("Missing port number! Try any number between 1024 to 49151");
31
            return;
32
        }
33
​
34
        int port = Integer.parseInt(args[0]);
35
​
36
        Server.start(port, new Handler());
37
    }
38
}
39
​```
40
​
41
**Screenshots**
42
​
43
![Image](Screenshot%202023-04-24%20at%201.17.28%20PM.png)
44
​
45
​
46
* The method addMessage was called.
47
​
48
* The relevant arguments to this method is just the site of the url. The values of the relevant field of the class, which is a String called s1, is a blank string.
49
​
50
* The value of s1 changes from this request by adding the message "Hello" and the escape sequences "/n" to make a new line without anything in it.
51
​
52
​
53
![Image](Screenshot%202023-04-24%20at%201.17.48%20PM.png)
54
​
55
​
56
* The method addMessage was called.
57
​
58
* The relevant arguments to this method is just the site of the url. The values of the relevant field of the class, which is a String called s1, is a string that includes the message from the first screenshot, which is "Hello".
59
​
60
* The value of s1 changes from this request by adding the message "Pasta Spaghetti Jambalaya Joodles Kelbow Alfredo" to the new line added from the frist added message and then added a new line for the next message.
61
​
62
​
63
# Part 2
64
​
65
**Failure-Inducing Input:**

```
@Test
  public void testReversed() {
    int[] input1 = {1, 2, 3, 4};
    assertArrayEquals(new int[]{ }, ArrayExamples.reversed(input1));
  }
66
​```

** Input That Doesn't Induce Failure:**

```
@Test
  public void testReversed2() {
    int[] input1 = {1};
    assertArrayEquals(new int[]{ }, ArrayExamples.reversed(input1));
  }
```


** Symptom:**

![Image](Screenshot%202023-04-24%20at%204.56.32%20PM.png)

** Bug**

Before:

```
static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }
```

After:

```
static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      newArray[i] = arr[arr.length - i - 1];
    }
    return newArray;
  }
```

This fixes the problem because now, the element that is being replaced is the element in the new array with the element from the original array unlike before where the code is just returning the original array with elements replaced with 0s.


# Part 3

Something that I learned from lab is how to make a server and write a code that could make changes to that server. In that topic, I learned how to access urls and modify them to fit my needs, like what queries I want to put and what the path should be. I also learned how to run that server on my computer with my account.
