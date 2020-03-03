---
attachments: [Clipboard_2020-02-17-10-09-31.png]
tags: [node JS]
title: JS Event Loop
created: '2020-02-17T03:53:07.445Z'
modified: '2020-02-17T04:57:44.084Z'
---

# JS Event Loop

Event loop receives events , calls necessary callbacks and offloads more expensive tasks to thread pool

Callback Queue : Callback coming from events received by event loop

![](@attachment/Clipboard_2020-02-17-10-09-31.png)

* Heap Memory Allocate memory for functions and variables
* Call Stack executes JS code in LIFO order
* Task Queue / Event Queue: Data Structure that holds callback functions to be executed ( FIFO )


## Event Loop

* Continuosly Running programme which monitors its queues
* Once the call stack is cleared, event loop picks a task from event queue and loads it into the task queue
* Each iteration in the event loop is called a tick

* DOM events are queued in event queue and Promises are queued in Microtask queue
* Call stack is executed first , Then even loop loads tasks from microtask to call stack . once both are empty, event loop loads tasks from task queue to call stack


* Task queue tasks : DOM ( onclick, onkeydown ) and Timer events ( setTimeout, setInterval )
* Micro tasks / Job : Promises ( resolve, reject ) , and Browser Observers ( Intersection Observer, Mutation Observer etc )

