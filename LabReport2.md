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



