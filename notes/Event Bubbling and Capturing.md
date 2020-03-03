---
tags: [Javascript]
title: Event Bubbling and Capturing
created: '2019-10-14T04:10:14.484Z'
modified: '2019-10-14T04:15:00.010Z'
---

# Event Bubbling and Capturing

* Two ways of evenrt propogation in the HTML DOM API.
* When an event occurs in an element inside another element, both elements have registered a handle to the event.
* With bubbling event is first captured and handled in the inenermost element (target) and then propogated to the outer elements (root).
* With capturing , event is first captured and handled at the outermost element (root) and then propogated to the outer element.
* Default event propogation is bubbling
