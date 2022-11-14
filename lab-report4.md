# Week 7 Lab Report

## Part 1

For the tasks from Week 6, I chose to complete the one where I had to change the main method to take in a command line argument.
In order to complete this task as fast as I could think of, I used the following commands:

`/pars<Enter>y$/".<Enter>d$"0pi))<<<<delete>1<esc>:wq`

This is what I typed to find what I wanted to copy:

![sc1](https://user-images.githubusercontent.com/114266346/201730808-1214b19d-f8fd-4b18-bdbd-10047244a706.png)

Then when I pressed enter it went to what I wanted to copy:

![sc2](https://user-images.githubusercontent.com/114266346/201730787-764cf0ea-f7ac-4f6f-a42d-58502e91d959.png)

I then pressed `y$` in order to copy from where the cursor was to the end of the line.
Then I search for what I wanted to replace using `/".`

![sc3](https://user-images.githubusercontent.com/114266346/201731290-6d588351-9c9e-49ae-b6bb-f8e194f17ee1.png)

Once I found it I used `d$` to delete everything from the cursor to the end of the line.

![sc4](https://user-images.githubusercontent.com/114266346/201731477-0c67a408-8a76-4630-a97e-50ebcf288dfc.png)

Then I typed `"0p` to paste what I had originally copied instead of what I just deleted.

![sc5](https://user-images.githubusercontent.com/114266346/201731742-64296e18-d92e-4313-a203-b7cac812db83.png)

I then pressed `i` to enter insert mode and I added a parenthesis and deleted the 0 and replaced it with 1 to take the second command line argument instead of the first:

![sc6](https://user-images.githubusercontent.com/114266346/201732107-cc5a4fa9-7ff9-4daf-85d7-64e101fd204a.png)

I then pressed `:wq` to save and quit.


## Part 2
When I tried editing the task in VSCode and then transferring it to the rmeote server via `scp`, it took 1:32 seconds.
Already starting logged in and editing through Vim took 1:18 seconds.

I think the Vim method took less time because I didn't have to go through the trouble of editing and then typing in the `scp` command and then typing in my username to login.
Using Vim took a shorter amount of time but I think it was because I had all the commands I needed already written down but in reality I'd have to look up which commands to use 
for everything which would obviously take longer. 

I also think that editing the file through VSCode just makes more sense in my brain so it's easier for me to see mistakes using
it. 

I can see how useful Vim is, especially when working on a remote server. I think if I knew the commands off the top of my head I would prefer it.





