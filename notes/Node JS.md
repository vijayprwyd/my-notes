---
attachments: [Clipboard_2020-02-10-17-39-14.png]
tags: [node JS]
title: Node JS
created: '2020-02-10T11:52:40.241Z'
modified: '2020-02-10T12:09:14.658Z'
---

# Node JS

* v8 engine converts Javascript code into machine code
* v8 written in JS and C++

libuv : 
* written in C++
* open source library with a strong focus on Asynchronous I/O.
* gives Node access to underlying OS , File system , networking and more .Implements * Event loop and thread loop for node

A node process running in a computer. Process is just a program of execution. Node JS runs ina single thread in the process.


* Some tasks are too heavy to be executed in event loop. Thats where thread pool comes in. 
* Thread pool gives 4 additional threads. ( can be increased upto 128 ).
* Event loop offloads heavy tasks to thread pool.
* Expensive tasks : File system, Cryptography, Compression adnDNS lookup

* Registering a callback  means you're passing a function to another program to call once it has finished processing some operation.

![](@attachment/Clipboard_2020-02-10-17-39-14.png)


