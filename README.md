# MutexServiceUsingRaymond
A mutual exclusion service using Raymond's tree-based distributed mutual exclusion algorithm. Used the already built spanning tree from one of my project to build the initial tree used by Raymond's algorithm. The service allows an application to request to start its critical section. Once request is granted the application can start executing its critical section. Once it is done, services allows the application to inform that it has finished executing its critical section.

-	The repository contains all the required .java files to compile and run the program.

-	It also contains the script files to launch and clean-up the process.

-	Along with all this files a configuration file “conf.txt” is there to help the program build the tree which later be used to start the mutual exclusion service.

To run:

a.	Keep all the file in a folder “AOS” under default location that is $HOME.

In my case it is (absolute location): /home/004/b/bx/bxs123330/AOS

b.	Compile the main program MutexMain.java

{dc01:~/AOS} javac MutexMain.java


c.	Once the program is compiled it generates all the required class file.

Now run the launcher script:

{dc01:~/AOS} sh launcher.sh


d.	It reads all the parameters from the configuration file. Inside which number of critical section requests per node, mean delay between two consecutive critical section requests and mean duration of critical section are also specified. In my case I have dedicated node 1 to be the holder of token for the first time (can be changed if needed).

e.	The service writes all its activity in the folder called “Critical_Section” and can be used to debug as well as check its overall activity node-wise.

/home/004/b/bx/bxs123330/AOS/Critical_Section

Logs on one run is there in the file.

f.	The file which we are interested to check for mutual exclusion property is “CS_Info.txt”.

g.	Once all the nodes are finished executing their CSs, we can check its correctness by:

{dc01:~/AOS} java UniqueLineReader

Its output would be similar to:
Number of Lines Read:300
File is correct

h.	Once it runs the specified times, use the clean-up script to kill the processes initiated by you and are still running in background.
{dc01:~/AOS} sh cleanup.sh

