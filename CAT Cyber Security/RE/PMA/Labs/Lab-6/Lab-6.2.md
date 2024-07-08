1- The first subroutine called by main is `sub_401000`, and it checks internet connection prints its state and proceeds to `sub_40117F`.

![](https://i.imgur.com/VY6ThAG.png)

2- It's almost identical `0x40105F` but a different subroutine is called which is `sub_4013A2`.

![](https://i.imgur.com/AiQLk04.png)


3- Checking `sub_401040` we can see it reads a file from internet, specifically `http://practicalmalwareanalysis.com/cc.htm`(which is also a network IOC).

![](https://i.imgur.com/eaS08sR.png)

reading the file from internet using [InteredReadFilefunction](https://learn.microsoft.com/en-us/windows/win32/api/wininet/nf-wininet-internetreadfile).

![](https://i.imgur.com/623o2SM.png)

4- Using graphical view we can see that there's an `if condition` with a `switch` statement

![](https://i.imgur.com/y6VyZLu.png)

We can see there's a `switch` statement with an `if style`  in the right side of the graph.

![](https://i.imgur.com/JUUqsIs.png)

5- The file read by `sub_401040`: `http://practicalmalwareanalysis.com/cc.htm`

6- Reading a file from `http://practicalmalwareanalysis.com/cc.htm` then checking its content for a specific command from: `<`, `!`, `-`, `-`.
