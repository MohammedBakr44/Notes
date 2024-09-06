---
share_link: https://share.note.sx/ws9v5yfa#RuA4R3rluNjnTzMe5dF9FU834fN82b+7t1+lO9dRssY
share_updated: 2024-08-04T02:34:46+03:00
---

1- The program uses services to achieve persistence. We can see it uses functions related to services.

![](https://i.imgur.com/mWiPqWj.png)

![](https://imgur.com/yLWrbIT.png) 


![](https://i.imgur.com/9ior2BO.png)


`OpenSCManager` establishes a connection with [service manager](https://learn.microsoft.com/en-us/windows/win32/api/winsvc/nf-winsvc-openscmanagera).

2- To ensure only one `thread` is executing malware logic.

3- The malware creates a service called `Malservice`, we can use that as a host-based IOC,

![](https://i.imgur.com/BqP5OKQ.png)

4- The malware starts a thread that access `http://www.malwareanalysisbook.com`.

![](https://i.imgur.com/Nm74ebE.png)


5- 
- The program starts by connecting to service manager using [`StartServiceCtrlDispatcherA`](https://learn.microsoft.com/en-us/windows/win32/api/winsvc/nf-winsvc-startservicectrldispatchera ); with a [`ServiceTable`](https://learn.microsoft.com/en-us/windows/win32/api/winsvc/ns-winsvc-service_table_entrya) that connects to `MalService` service. then it calls a `subroutine`  at address `0x401040` which contains the main logic of the malware.

![](https://i.imgur.com/IfgVJ7V.png)

- `0x401040` will start by looking for `Mutex` called `HGL35`, if it's found(there's another thread running the logic) the program will exit, else it will jump to `0x401064`.

![](https://i.imgur.com/nXiefgM.png)

- `0x401064` starts by creating `HGL345` Mutex.

![](https://i.imgur.com/3WZbEXX.png)

Then it creates the service `MalService` which executes the current running process.

![](https://i.imgur.com/uEOo4MN.png)

A [`Waitable Timer`](https://learn.microsoft.com/en-us/windows/win32/sync/waitable-timer-objects) is created, and then `WaitForSigleObject` is used to enter a wait state indefinitely; waiting for the `Waitable Timer` to signal, if it did signal, then `CreateThread` will be run, else the program terminates by jumping to `0x40113B`.

![](https://i.imgur.com/ZnhRizX.png)

5- The program never finish executing,`WaitforSingleObject` is waiting indefinitely, there's an infinite loop in the `startAddress`. However, the program my finish immediately if it failed to create a timer.

![](https://i.imgur.com/v1aJBnw.png)
