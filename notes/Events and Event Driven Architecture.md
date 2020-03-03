---
attachments: [Clipboard_2020-03-03-09-48-21.png]
tags: [node JS]
title: Events and Event Driven Architecture
created: '2020-03-03T04:09:09.686Z'
modified: '2020-03-03T04:18:21.905Z'
---

# Events and Event Driven Architecture

* Most of the node modules like http. file system and timers are built on event driven architecture
* Event Emitters : emit named events when something happens
* Event Listeners : Picks the events and fires the callback
* Called Observer pattern in JS



![](@attachment/Clipboard_2020-03-03-09-48-21.png)

* Server ( instance of EventEmitter class)  emits an event called **request**  each time a request hits the server.
* Observer keeps observing the subject
