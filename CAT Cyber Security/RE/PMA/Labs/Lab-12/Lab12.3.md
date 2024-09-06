1- The sample shows signs of keylogging activity.

As we can see from these imports

![](https://i.imgur.com/J9gIWAF.png)


![](https://i.imgur.com/ia1jLFv.png)

There are also some keycodes stored in sample's string.

![](https://i.imgur.com/i8Sm6GG.png)

Going further with *Advanced Static Analysis* we can see that the sample creates a file called `practicalmalwareanalysis.log`

![](https://i.imgur.com/04WD9Zz.png)


The sample checks for the foreground window's title using `GetWindowsTextA` function and stores it in the file with format `\r\n[Window: ${GetWindowTextA}]\r\n`

![](https://i.imgur.com/ZZWJrDn.png)

![](https://i.imgur.com/iJBq9Xy.png)


3- It creates a file called `practicalmalwarenalysis.log`.