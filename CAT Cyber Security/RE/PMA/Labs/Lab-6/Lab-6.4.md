1, 2- Lab-6.4 contains a while loop that compares `eax` with the argument and increments it. 

![](https://i.imgur.com/hV4oTl2.png)

loop step, returns to the start of the loop after `100000`ms of `sleep`.

![](https://i.imgur.com/qufqKsd.png)

We can clearly see it using graph view as well

![](https://i.imgur.com/rD0HAvz.png)

3- The function in lab-6.4 prints something; as it's calling `_sprintf`.

![](https://i.imgur.com/PkPJgYW.png)

4- The program sleeps for `60000ms` (1 minute) every iteration.

![](https://i.imgur.com/v3yKVMM.png)

And it runs for `1440` iteration, so it runs once every minute for `1440` minute which is 24 hours.

![](https://i.imgur.com/U1VABeZ.png)

5- No, there's only `http://practicalmalwareanalysis.com/cc.htm` which hosts the commands file.

6- The malware starts by checking internet access, if the infected machine is connected to internet, it starts a loop, otherwise it terminates.

![](https://i.imgur.com/Ba5kl71.png)

We can see it graphically in this part

![](https://i.imgur.com/ik0naKE.png)

We can see the increment step of the loop here:

![](https://i.imgur.com/AatuVxK.png)

The body starts with a condition, comparing `i` with 1440 and `jge` works as a terminating condition (1).

![](https://i.imgur.com/AIiJt0R.png)

Then it reads a file that contains commands from `http://practicalmalwareanalysis.com/cc.htm` 
if the function returned with no errors, then it jumps to another block renamed `fileParsaeAndCommandRun` (3), with the same error checking mechanism as 2, if anything went wrong the program terminates.

The next block starts the real function of the malware, it starts by parsing a file  (1) that will be sent to `commandRun` in order to run one of the mentioned commands in lab-6.3.3, rest of the code is responsible for sleeping for a minute and then restarting the loop. (2)

![](https://i.imgur.com/djWs1QT.png)

We can confirm this flow from the graphical view of main function.

![](https://i.imgur.com/d4SLXb1.png)