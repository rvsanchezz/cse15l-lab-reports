# grade.sh code:

My grade.sh file contained the following code

```

set -e

rm -rf student-submission
git clone $1 student-submission

classpath=".:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar"

cd student-submission

if test -f ListExamples.java 
then
    echo "ListExamples.java file exists"
else
    echo "ListExamples.java does not exist"
    exit 1
fi

cp ListExamples.java ../

cd ..
javac -cp $classpath TestListExamples.java ListExamples.java

if test $? -eq 0
then
    echo "Compiled successfully !"
else 
    echo "Compile unsuccessful :("
    exit 1
fi

set +e

echo "Running tests now"

java -cp $classpath org.junit.runner.JUnitCore TestListExamples > scores.txt


grep -n "Error:" scores.txt
score=$(grep -c "Error" scores.txt)

if "$score" = "0";
then
    echo "Score = 100%"
else
    echo "Score = 75%"
fi
```

The first student submission (https://github.com/ucsd-cse15l-f22/list-methods-lab3) gave the following output:
![img](https://user-images.githubusercontent.com/114266346/204203901-9ae5adf7-e6bd-4656-8057-9c9f2719ca7c.png)

Another submission (https://github.com/ucsd-cse15l-f22/list-methods-corrected) gave this output:
![img2](https://user-images.githubusercontent.com/114266346/204204300-b0088eec-bda6-4ca9-90f0-ab96e58e2286.png)

Lastly, a submission containing the method under the wrong filename (https://github.com/ucsd-cse15l-f22/list-methods-filename) gave the following message:
![img3](https://user-images.githubusercontent.com/114266346/204204850-54ece682-b4e5-4849-8437-ce6a610899e7.png)

Following grade.sh on the last repository, the standard output was "ListExamples.java does not exist, Failed".
The standard error was not printed but is a No such file or directory case.
The return code was nonzero since the if statement was false.
Any lines after the end of the if statement (line 17) was not run.
