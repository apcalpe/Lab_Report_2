

# Part 1

**Code:**

```
import java.io.IOException;
import java.net.URI;


class AddMessages implements URLHandler {

    String s1 = "";
    
    public String addMessage(URI url) {
    
        if (url.getPath().equals("/add-message")) {

            String[] parameters = url.getQuery().split("=");

                s1 = s1 + parameters[1] + "\n";
                return s1;
        }
        
        return "Add a message!";
    }
}


class StringServer {

    public static void main(String[] args) throws IOException {

        if(args.length == 0){

            System.out.println("Missing port number! Try any number between 1024 to 49151");

            return;

        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}
```

**Screenshots**

![Image](Screenshot%202023-04-24%20at%201.17.28%20PM.png)


* The method addMessage was called.
* The relevant arguments to this method is just the site of the url. The values of the relevant field of the class, which is a String called s1, is a blank string.
* The value of s1 changes from this request by adding the message "Hello" and the escape sequences "/n" to make a new line without anything in it.

![Image](Screenshot%202023-04-24%20at%201.17.48%20PM.png)

* The method addMessage was called.
* The relevant arguments to this method is just the site of the url. The values of the relevant field of the class, which is a String called s1, is a string that includes the message from the first screenshot, which is "Hello".
* The value of s1 changes from this request by adding the message "Pasta Spaghetti Jambalaya Joodles Kelbow Alfredo" to the new line added from the frist added message and then added a new line for the next message.


# Part 2

**Failure-Inducing Input:**

```
@Test
  public void testReversed() {
    int[] input1 = {1, 2, 3, 4};
    assertArrayEquals(new int[]{ }, ArrayExamples.reversed(input1));
  }
```

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

This fixes the problem because now, the element that is being replaced is the element in the new array with the element from the original array unlike before where the code is just returning the original array with elements replaced with 0s.

