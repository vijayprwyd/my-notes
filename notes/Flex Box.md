---
attachments: [Clipboard_2019-11-24-11-26-34.png, Clipboard_2019-11-24-11-26-45.png, Clipboard_2019-11-24-11-40-05.png, Clipboard_2019-11-24-13-08-23.png, Clipboard_2019-11-24-13-58-22.png, Clipboard_2019-11-24-14-00-54.png, Clipboard_2019-11-24-14-32-51.png, Clipboard_2019-11-24-14-41-04.png, Clipboard_2019-11-24-18-54-49.png, Clipboard_2019-11-24-19-43-33.png, Clipboard_2019-11-24-21-00-47.png, Clipboard_2019-11-24-21-01-10.png]
tags: [CSS]
title: Flex Box
created: '2019-11-24T05:35:08.477Z'
modified: '2019-11-24T15:31:12.605Z'
---

# Flex Box

Flexible responsive layout.

1. **flex-direction** (row, row-reverse, column, column-reverse)
2. **flex-wrap** (nowrap, wrap, wrap-reverse)
3. **flex-flow**
4. **justify-content** ( flex-start, center, flex-end, space-between, space-around, space-evenly)
5. **align-items** ( flex-start, flex-end, center, baseline, stretch )
6. **align-content** ( center, space-around, space-between, space-evenly, baseline, flex-start, flex-end)
7. **flex-grow** ( number )
8. **flex-shrink** 
9. **flex-basis**
10. **align-self**
11. **flex**

```html
<div style = "display:flex">
   <div> 1 </div>
   <div> 2 </div>
   <div> 3 </div>
</div>

```

## flex-direction 

Specifies the direction in which container wants to stack the flex items

* row  (default)
* row-reverse
* column
* column-reverse

![](@attachment/Clipboard_2019-11-24-11-26-34.png)

![](@attachment/Clipboard_2019-11-24-11-26-45.png)

## flex-wrap

Specifies whether the flex items should wrap or not

* no-wrap
* wrap
* wrap-reverse

![](@attachment/Clipboard_2019-11-24-11-40-05.png)

## flex-flow

Shorthand for specifying flex direction and flex wrap properties

`eg : flex-flow: row wrap `

## justify-content

Align the flex items on the main axis

* flex-start (default) : Start from the begining of the flex line
* flex-end: Start from the end of the flex line
* center: Move the flex items to the center
* space-between: Fist item start of the line, last item end of the flex line, other items evenly spaced in the line
* space-around: Space around the flex items evenly distributed.
* space-evenly: Space between adjacent elements evenly distributed

![](@attachment/Clipboard_2019-11-24-13-08-23.png)

## align-items

Align flex items vertically

* center: Center flex items vertically
* flex-start: Vertically align flex items to top
* flex-end: Vertical align flex items to bottom
* baseline: Vertical align flex items along contents baseline
* stretch (default): Stretches flex items

![](@attachment/Clipboard_2019-11-24-13-58-22.png)

![](@attachment/Clipboard_2019-11-24-14-00-54.png)

## align-content

Aligns flex items when there is an extra space on the cross axis. Used to align flex lines

* flex-start
* flex-end
* baseline
* center
* space-around
* space-between
* space-evenly

![](@attachment/Clipboard_2019-11-24-14-32-51.png)

![](@attachment/Clipboard_2019-11-24-14-41-04.png)

## flex-grow

Specifies how remaining space in flexbox container should be assgined to flex items

![](@attachment/Clipboard_2019-11-24-18-54-49.png)

## flex-shrink

Specifies how much flex items should shrink relative to each other if they are unable to fill in the parent container
Default flex shrink = 1


![](@attachment/Clipboard_2019-11-24-19-43-33.png)

## flex-basis

Initial Length of a flex item

## align-self

Overrides align-items property set by the parent container

![](@attachment/Clipboard_2019-11-24-21-01-10.png)


## flex

Shorthand for flex-grow flex-shrink and flex-basis property

`flex: 1 1 70%`









