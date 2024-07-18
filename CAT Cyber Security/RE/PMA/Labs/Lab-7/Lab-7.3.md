
| filename     | hash(SHA-256)                                                    | VT                                                                                                            | Packing |
| ------------ | ---------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- | ------- |
| Lab07-03.exe | 3475CE2E4AAA555E5BBD0338641DD411C51615437A854C2CB24B4CA2C048791A | [54/74](https://www.virustotal.com/gui/file/3475ce2e4aaa555e5bbd0338641dd411c51615437a854c2cb24b4ca2c048791a) | No      |
| Lab07-03.dll | F50E42C8DFAAB649BDE0398867E930B86C2A599E8DB83B8260393082268F2DBA | [47/74](https://www.virustotal.com/gui/file/f50e42c8dfaab649bde0398867e930b86c2a599e8db83b8260393082268f2dba) | No      |

## Basic Static Analysis
Looking at both files, we can see that the main functionality are coded in `.dll` file, it utilises `Mutex` and connects to network.

![](https://i.imgur.com/0y2HPzN.png)

As the imports indicates, some file manipulation functions are being used in the executable.

![](https://i.imgur.com/BH1rsH9.png)

Looking at the strings of `.exe` we can see there's a path to `C:\windows\system32\kerne132.dll` we can use this as a host-based IoC.
`

![](https://i.imgur.com/RNtQvl6.png)

Looking strings of `.dll` file, we can see an IP `127.26.152.13` which we can use a network-based IoC.

![](https://i.imgur.com/Z4mKCCl.png)


## Basic Dynamic Analysis

![](https://i.imgur.com/FcM0qDt.jpeg)


## Advanced Static Analysis

We start with `.exe` file, which is used to access files, namely `lab07-03.dll` and `C:\\Windows\\System32\\Kernel32.dll`. 

![](https://i.imgur.com/nYbZvbK.png)

It looks for `Lab07-03.dll` and terminates if didn't find it.

Then a file(most probably `Lab-07-03.dll`) is accessed through `MapViewOfFile` function, then there's a loop which alters file content or looks for something inside it.

![](https://i.imgur.com/UCBaWM5.png)

This logic leads to the final block of the program

![](https://i.imgur.com/Ypa152t.png)

In which the file `Lab-07-03.dll` is copied to `C:\\windows\\system32\\` as `kerne132.dll`.