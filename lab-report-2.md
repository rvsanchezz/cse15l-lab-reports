# Part 1
## Simple Search Engine

Search Engine Code
```
import java.io.IOException;
import java.net.URI;
import java.util.*;

class Handler implements URLHandler {
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.
    List<String> strList = new ArrayList<String>();

    // Tracks a list of strings
    // Support a path for adding a new string to the list
    // A path for querying the list of string and returning a list of all strings
    // that have a given substring.

    public String handleRequest(URI url) {
        if (url.getPath().contains("/")) {
            if (url.getPath().contains("add")) {
                String[] parameters = url.getQuery().split("=");
                if (parameters[0].contains("s")) {
                    if (parameters[1].contains("anewstringtoadd")) {
                        strList = new ArrayList<String>();
                        return String.format("%s", strList);
                    } else {
                        strList.add(parameters[1]);
                        return String.format("%s", strList);
                    }
                } else {
                    return "404 Not Found!";
                }
            } else if (url.getPath().contains("search")) {
                String[] parameters = url.getQuery().split("=");
                List<String> found = new ArrayList<String>();

                if (parameters[0].contains("s")) {

                    for (String str : strList) {
                        if (str.contains(parameters[1])) {
                            found.add(str);
                        }
                    }
                }
                return String.format("%s", found);

            } else {
                return String.format("%s", strList);
            }
        }
        return "404 Not Found!";
    }
}

class NumberServer {
    public static void main(String[] args) throws IOException {
        if (args.length == 0) {
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}
```


![sc1](https://user-images.githubusercontent.com/114266346/195961330-df135856-5850-40e8-b21d-655d76a7c9d6.png)
In this screenshot I was adding a string to the list. This uses this part of the code:

```
else {
  strList.add(parameters[1]);
  return String.format("%s", strList);
}
```
This part of the code essentially adds the string to a previously made list. 
The previous conditional statements have already checked if it is an acceptable string to add.

![sc2](https://user-images.githubusercontent.com/114266346/195962000-3c19648d-eb74-4d1a-98a8-61aeaaf93892.png)

In the above screenshot you can see that I added multiple words to the list. Now when I type `/search?s=pine`, it will return any words containing that substring.
![sc2](https://user-images.githubusercontent.com/114266346/195962150-10453ecf-f45c-4cf9-afa6-9ea09bcdcc45.png)

This action is done by this part of the code:
```
else if (url.getPath().contains("search")) {
      String[] parameters = url.getQuery().split("=");
      List<String> found = new ArrayList<String>();

      if (parameters[0].contains("s")) {

        for (String str : strList) {
          if (str.contains(parameters[1])) {
            found.add(str);
          }
         }
       }
      return String.format("%s", found);
```
Now, when I type `/add?s=anewstringtoadd` it will clear the list of all previous entries.
![sc4](https://user-images.githubusercontent.com/114266346/195962310-06f600d8-aefb-401b-838e-8c72eda4f800.png)

# Part 2
## Bugs and Symptoms

In ArrayExamples.java, an example reverseInPlace test would look something like this
```
@Test 
public void testReverseInPlace() {
    int[] input1 = {1, 2, 3};
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{3, 2, 1}, input1);
	}
 ```
 with any array as an input and the exact array but with all of the values in reverse as the expected output. This would be the failure inducing input.
 
 This is the code the previous test is trying to test:
 ```
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
```

The symptom is shown in this run of the tests:
![sc5](https://user-images.githubusercontent.com/114266346/195962631-011a7066-379a-4261-94e6-5cef7db93dc4.png)

The array does not seem to be swapping the elements.

When you look closer at the code, you see that there are two bugs. 
First in the for loop, it is iterating through the whole loop and swapping when it should only go through half so it does not swap the elements back to their original place.

The second bug is in this line `arr[i] = arr[arr.length - i - 1];`
It is assigning the last value to the first index of the array, yet does not assign the first value to the last index of the array.

The bug and symptom are related because the symptom shows how the last index of the array was not reassigned the first index's value, resulting in the element being 3 when it should have been 1.


In the ListExamples file this was the failure inducing input I used:
```
@Test
    public void filter2() {
        List<String> input = new ArrayList<>();
        List<String> expected = new ArrayList<>();

        StringChecker sc = new checkString();

        input.add("sandwich");
        input.add("crab");
        input.add("sand");
        input.add("Towers");
        expected.add("sandwich");
        expected.add("Towers");
        assertEquals(expected, ListExamples.filter(input, sc));
    }
```

This was the symptom I got:
![sc6](https://user-images.githubusercontent.com/114266346/195963649-0385c7ee-c361-43e6-a5e7-628ebaa28ef4.png)

It is giving an error because the bug is that there was never a StringChecker implementation. A new class would have to be created that implements StringChecker.
