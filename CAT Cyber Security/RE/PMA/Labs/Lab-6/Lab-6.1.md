1- an if condition that checks if internet is connected or not.

![](https://i.imgur.com/wJGYlDl.png)

2- A function that takes two integer arguments, as the difference between them is 4 bytes

![](https://i.imgur.com/8jzy8tr.png)

3- The program starts by checking for internet connection by calling `sub_401000`.

![](https://i.imgur.com/1X5bySY.png)

Then `sub_401000` checks for internet connection prints a message stating connection status and then proceeds to `sub_40105F`

![](https://i.imgur.com/R2yx8CN.png)

 Then a couple of functions are called `__stbuf`, `__sub_401282`, `__ftbuf`, respectively.
 
 ![](https://i.imgur.com/5UalHOw.png)

All of the functions are called with a parameter of a memory address of file stored in `esi`, it looks like they are editing the file in someway.

The function `__sub_401282`, is a huge `jumptable` indicating a switch case with 8 branches

![](https://i.imgur.com/jSnP4nc.png)

start of `jumptable`

![](https://i.imgur.com/33PzdJn.png)

Looking at some of the branches it looks like the file is being searched for some specific characters

![](https://i.imgur.com/4mzD4sV.png)
