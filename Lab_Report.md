# Part 1

**Code:**

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


