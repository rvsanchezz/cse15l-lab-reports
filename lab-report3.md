# Lab Report 3

## Using `grep -i`

`grep -i` can be used to find a specific string within a file.

When I searched for the word "war" I was given a large piece of the file's contents.

```
raquelsanchez@Raquels-MacBook-Pro docsearch % grep -i "war" technical/911report/chapter-2.txt
A DECLARATION OF WAR
                declared war against God and his messenger, they called for the murder of any
                shall-with the grace of Allah-prevail over the Americans." He went on to warn that
                the Messenger and to communicate his message to all nations," and to serve as the rallying point and organizer of a new kind of war to
                Iraqi people as a result of sanctions imposed after the Gulf War, and he protested
            Denouncing waywardness among the faithful, some clerics have appealed for a return to
                jahiliyya. Second, he warned that more people, including Muslims, were attracted to
                of mankind." If the United States did not comply, it would be at war with the
                the overwhelmingly secular struggles for independence after World War I.         
```

In comparison, when I searched for a word that was not in the file, nothing was outputted. 

```
raquelsanchez@Raquels-MacBook-Pro docsearch % grep -i "hello" technical/911report/chapter-2.txt
raquelsanchez@Raquels-MacBook-Pro docsearch % 
```

I also tried searching for a number in another file

```
raquelsanchez@Raquels-MacBook-Pro docsearch % grep -i "1986" technical/911report/chapter-5.txt
                    1986.
                jihad by sending him to Afghanistan in 1986. After undergoing training at Rasul
```

After trying these inputs, I realized that the output is every line containing the given string, even words with the string within it. In the first example
most of the lines did not have the word "war", but words with that substring such as "wayward". 
This command can be very helpful when someone is looking for information on something but they can't quite remember where in a file it is. They can
use this command to find it within the file and the context surrounding it.

## Using `grep -l`

Instead of returning a specific file's contents with a word, you can use `grep -l` to find every file containing the input string.


This is the output I got using "sulfasalazine" as an input.
```
raquelsanchez@Raquels-MacBook-Pro docsearch % grep -l "sulfasalazine" technical/biomed/*
technical/biomed/1471-230X-1-8.txt
technical/biomed/1472-6963-3-14.txt
technical/biomed/ar430.txt
```
  
Here is another example in a different directory and its subdirectories.
```
raquelsanchez@Raquels-MacBook-Pro docsearch % grep -l "alcohol" technical/government/*/*
technical/government/Alcohol_Problems/DraftRecom-PDF.txt
technical/government/Alcohol_Problems/Session2-PDF.txt
technical/government/Alcohol_Problems/Session3-PDF.txt
technical/government/Alcohol_Problems/Session4-PDF.txt
technical/government/Gen_Account_Office/og97002.txt
technical/government/Media/Abuse_penalties.txt
technical/government/Media/Annual_Fee.txt
technical/government/Media/Higher_Registration_Fees.txt
technical/government/Media/Paralegal_Honored.txt
technical/government/Media/Weak_economy.txt
```    

I also tried using a number in this directory as well.
```
raquelsanchez@Raquels-MacBook-Pro docsearch % grep -l "127" technical/government/*/*
technical/government/About_LSC/commission_report.txt
technical/government/Alcohol_Problems/Session2-PDF.txt
technical/government/Alcohol_Problems/Session4-PDF.txt
technical/government/Env_Prot_Agen/tech_adden.txt
technical/government/Gen_Account_Office/May1998_ai98068.txt
technical/government/Gen_Account_Office/Sept14-2002_d011070.txt
technical/government/Gen_Account_Office/Statements_Feb28-1997_volume.txt
technical/government/Gen_Account_Office/ai2132.txt
technical/government/Gen_Account_Office/ai9868.txt
technical/government/Gen_Account_Office/d01186g.txt
technical/government/Gen_Account_Office/d01591sp.txt
technical/government/Gen_Account_Office/im814.txt
technical/government/Gen_Account_Office/og96011.txt
technical/government/Gen_Account_Office/og96031.txt
technical/government/Gen_Account_Office/og96047.txt
technical/government/Gen_Account_Office/og97001.txt
technical/government/Gen_Account_Office/og97002.txt
technical/government/Gen_Account_Office/og98024.txt
technical/government/Gen_Account_Office/pe1019.txt
```

This command is used to find all of the files that contain the string you input. This is extremely useful if doing research and you want to find 
all the texts and files that contain the issue you are writing or looking for information on.

## Using `grep -n`

This command finds the texts and lines that a certain string is on.

```
raquelsanchez@Raquels-MacBook-Pro docsearch % grep -n "ALLHAT" technical/biomed/*
technical/biomed/1468-6708-3-10.txt:7:        Prevent Heart Attack Trial (ALLHAT) is a randomized,
technical/biomed/1468-6708-3-10.txt:72:          The rationale and design of ALLHAT are described in
technical/biomed/1468-6708-3-10.txt:96:          1. Did HF cases meet ALLHAT diagnostic criteria?
technical/biomed/1468-6708-3-10.txt:117:          were reviewed at the ALLHAT Clinical Trials Center (CTC)
technical/biomed/1468-6708-3-10.txt:124:          ALLHAT Endpoints Subcommittee; for these cases additional
technical/biomed/1468-6708-3-10.txt:147:          The ALLHAT definition of HF, used previously in the
technical/biomed/1468-6708-3-10.txt:379:        created a dilemma for ALLHAT. Since the trial was not
technical/biomed/1468-6708-3-10.txt:405:        ALLHAT criteria for HF were equivalently met in the two
```

The previous example contained many more lines considering "ALLHAT" was the main focus in this file.

```
raquelsanchez@Raquels-MacBook-Pro docsearch % grep -n "R26R" technical/biomed/*
technical/biomed/1471-213X-1-4.txt:11:        lacZ reporter strain (R26R) was
technical/biomed/1471-213X-1-4.txt:16:        R26R allele terminates transcription
technical/biomed/1471-213X-1-4.txt:77:        colonies were analyzed for each construct. Three R26R-EYFP
technical/biomed/1471-213X-1-4.txt:78:        and two R26R-ECFP colonies carried the targeted allele, as
technical/biomed/1471-213X-1-4.txt:87:        detected in the R26R-EYFP or R26R-ECFP mice, as expected
technical/biomed/1471-213X-1-4.txt:104:        The specificity of the R26R-EYFP and ECFP lines was
technical/biomed/1471-213X-1-4.txt:116:        25]. Figure 3Ashows an experiment in which the R26R-YFP
technical/biomed/1471-213X-1-4.txt:119:        in the doubly transgenic offspring. Thus R26R-YFP mice
technical/biomed/1471-213X-1-4.txt:123:        R26R lacZ allele [ 4], resulting in a
technical/biomed/1471-213X-1-4.txt:130:        R26R-YFP mice were crossed with a strain of mice in which
technical/biomed/1471-213X-1-4.txt:136:        R26R lacZ allele [ 4], resulting in
```

```
raquelsanchez@Raquels-MacBook-Pro docsearch % grep -n "trial" technical/biomed/*
technical/biomed/1468-6708-3-7.txt:249:        the ALLHAT trial were unexpected, given the potential
technical/biomed/1468-6708-3-7.txt:274:        increasing the incidence of CHF in the ALLHAT trial, it
technical/biomed/1468-6708-3-7.txt:313:        a member of the Events Committee of the HERS trial funded
technical/biomed/1471-2105-3-26.txt:19:        response stratification of patients in clinical trials,
technical/biomed/1471-2105-4-13.txt:77:        every trial described throughout this work. The fact that
technical/biomed/1471-2105-4-24.txt:396:        trials without generating an unacceptably high false
technical/biomed/1471-2105-4-28.txt:37:          trial-and-error approach iscommonly employed for
```

The previous example is also a small portion of the actual input, however it was important to show that it returns every file and 
line number that contains the specific string. You can see how the different files are given and then the line number and then the
actual text on that line. This is an important functions because it allows the user to easily find what they are looking for within
the different files.
