# Lab Report 2 - Servers and SSH Keys

## Part 1

This is the StringServer code.
```
import java.io.IOException;
import java.net.URI;

class Handler implements URLHandler {
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.
    int num = 1;
    String msg = "";

    public String handleRequest(URI url) {

        if (url.getPath().equals("/")) {
            if (msg.equals("")) {
                return "No messages yet.";
            }
            return msg;
        } else {
            if (url.getPath().contains("/add-message")) {
                String[] parameters = url.getQuery().split("=");
                if (parameters[0].equals("s")) {
                    if (num==1) {
                        msg += num + ". " + parameters[1];
                        num++;
                        return msg;
                    } else { 
                        msg += "\n" + num + ". " + parameters[1];
                        num++;
                        return msg;
                    }
                }
            }
            return "404 Not Found!";
        }
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


**First Screenshot**

![First code screenshot](https://github.com/Lope879/cse15l-lab-reports/assets/100965607/5826642f-cd2b-48f4-96ca-bc2787112a52)

The methods handleRequest and main are called in my code. 
The relevant argument to handlerequest is the url of the website being displayed, with values of its class being num, msg and url. 
The relevant argument to main is the port of the website being started.
After this request, the value num changed from 1 to 2 since the 1 was used to be displayed before the first message,
the value msg changed from an empty string ("") to the message "1. Hello first test.", 
and finally url got changed to its current link address ending in "s=Hello%20first%20test." instead of having no arguments.


**Second Screenshot**

![Second code screenshot](https://github.com/Lope879/cse15l-lab-reports/assets/100965607/93aa66ab-3d23-4757-9524-7d0fc90701f6)

The methods handleRequest and main are still called in my code. 
The relevant argument to handlerequest remains being the url of the website being displayed, with values of its class being num, msg and url. 
The relevant argument to main remains being the port of the website being started.
After this request, the value num changed from 2 to 3 since the 2 was used to be displayed before the second message,
the value msg changed from its previous string to the message "1. Hello first test. \n 2. Second test", 
and finally url got changed to its current link address with query ending in "s=Second%20test" instead of its previous argument.



## Part 2

Path to private key in my computer

![Path to private key in my computer](https://github.com/Lope879/cse15l-lab-reports/assets/100965607/04af7591-7ecb-474f-8b61-06aa2313eee3)

Path to public key in remote computer

![Path to public key in remote computer](https://github.com/Lope879/cse15l-lab-reports/assets/100965607/a3eb445b-06d3-4c5d-8343-7f9963afe4f1)

Login without password

![Login without password](https://github.com/Lope879/cse15l-lab-reports/assets/100965607/1fb5b1cf-809e-4ccb-ad94-ca45136b5505)


## Part 3

Some things I learned from lab 2 that I didn't know before are things such as connecting to a remote server from my terminal, creating a server, 
running the server, and interacting with content inside the remote terminal. To connect to a remote server I need to use command ssh which I was able to use 
for the UCSD remote server using my personal ucsd account. 

Some things I learned from lab 3 are learning how to run a server from my computer and being able to interact with it using my browser, 
as well as learning how to copy a file from my terminal to a remote terminal.
