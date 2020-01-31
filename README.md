# feynman
Feynman is tests submission interface for Ruangguru Tech interview.

## INSTALLATION

Download your *feynman* distribution:

* Linux
    * File:
    * Checksum:
* Windows
    * File:
    * Checksum:
* OSX
    * File: 
    * Checksum: 

Rename downloaded file to *feynman*, add executable permission to it, then place the file into your execution PATH or working directory.

*Installation notes on OSX Catalina:*

If you encounter this warning during *feynman* execution:

Please follow these additional steps:

* Open finder
* Go to your download target directory
* Option+Click your feynman binary file
* Choose Open

## CONFIGURATION

Upon completing registration on <registrationURL> you will receive an authentication token. Use this token to configure your *feynman* session.

```sh
feynman configure <token-string>
```
  
## DOWNLOADING TEST

To start working on the tests, you need to download the challenge first. You could initiate download using: 
```sh
feynman download
> Downloading Challenges...
> Downloaded Internship Test 3/i1/i1-problem.html contains 266 bytes
> Downloaded Internship Test 3/i1/i1-small.in contains 32 bytes
> Downloaded Internship Test 3/i1/i1-large.in contains 25 bytes
> Downloaded Internship Test 3/i1/i1-small.out contains 44 bytes
> Downloaded Internship Test 3/i1/i1-large.out contains 44 bytes
```

Each event may have different set of challenge. For each challenge, *feynman* will create a folder, and store each related files under that folder.

Folder structure examples:
```
- your current working directory
  - Event Name
    - Challenge #1
      - ch1-problem.html
      - ch1-small.in
      - ch1-small.out
      - ch1-large.in
      - ch1-large.out
    - Challenge #2
    ...
```
### Downloaded Files

* Problem File (.html): contains problem statement of the challenge, please read the instruction using your favorite browser
* Input Files (*.in): contains input that will be processed by your application. Formats may varies, please refer to problem statements.
* Output Files (*.out): contains output example. Please refer to challenge’s problem statement to see the valid output formats.

## SOLVING THE PROBLEMS

After completing each of the steps above, you are now ready to do some code. You could use any programming language to solve the problem. Just make sure that it will outputs the result to output example files provided inside the challenge directory.
```sh
yourapp < ch1-small.in > ch1-small.out
yourapp < ch1-large.in > ch1-large.out
```

## SUBMIT SOLUTIONS

Right after you solve the problem, you may submit your solution and Output(.out) files, make sure you're using the same filename convention — <challengeID>-<small|large>.out.

You could submit your solution multiple times, during the event start and end time.
```sh
feynman submit p1-small.out
```
Feynman will renders your submission result file.
```sh
Upload Status: 'i1-small.out'
Passed: false
Messages:
FAILED Test Case #1
FAILED Test Case #2
```
Please note that after submitting large.out files, *feynman* only renders submission status, without any SUCCESS/FAILED notification on each test case
```sh
Upload Status: '/tmp/Internship Test 3/i1/i1-large.out'
Passed: false
Messages:
Submitted, results will be calculated after the event end. 
You can still re-submit your solution before the event end
```
## SHOW RESULTS

You could tell *feynman* to show your submission status using *info* command. It will renders each available event and challenge that linked to your authorization token.

It will prints this following info:

* Your name and email address
* Contact Person information: please contact this number/email if you encounters any problem during submission.
* Active Events
    * Challenge Submission status for each file.
* Past Events, and 
* Upcoming Events.

```sh
feynman info
Logged in as <user> - (<userEmail>)

# Active Events
-------------------------------------------------------------
 1. Internship Test 3                      
    CP: <email> (<phoneNumber>) 
    Total Score: 10                        
-------------------------------------------------------------
    Challenge: Why life is easy?                      
-------------------------------------------------------------
    FILENAME                                STATUS     SCORE 
    i1-small.out                            Success    10    
    i1-large.out                            Submitted  10    
-------------------------------------------------------------

# Past Events
-----------------------------------------------------------------
 1. Internship Test 1                      
    CP: <email> (<phoneNumber>)  
    Total Score: 0                         
-----------------------------------------------------------------
    Challenge: Why life is easy?                          
-----------------------------------------------------------------
    FILENAME                                STATUS         SCORE 
    i1-small.out                            Not Submitted  10    
    i1-large.out                            Not Submitted  20    
-----------------------------------------------------------------
 2. Internship Coding Test July 2020       
    CP: <email> (<phoneNumber>)  
    Total Score: 30                        
-----------------------------------------------------------------
    Challenge: Why life is easy?                          
-----------------------------------------------------------------
    FILENAME                                STATUS         SCORE 
    i1-small.out                            Not Submitted  10    
    i1-large.out                            Not Submitted  10    
-----------------------------------------------------------------
    Challenge: Practice Question 1                        
-----------------------------------------------------------------
    FILENAME                                STATUS         SCORE 
    practice-1-small.out                    Not Submitted  10    
    practice-1-large.out                    Not Submitted  10    
-----------------------------------------------------------------
    Challenge: Think different                            
-----------------------------------------------------------------
    FILENAME                                STATUS         SCORE 
    think-different-small.out               Not Submitted  10    
    think-different-large.out               Not Submitted  10    
-----------------------------------------------------------------
```

## PRACTICE MODE

Practice mode simply mock each functionality of the real test. Feynman will not include the result to passing score criteria. It is only a testing sandbox. You could play around with it freely :)
```sh
feynman info —practice
feynman download —practice
feynman submit --practice Practice/p1/p1-large.out
```

