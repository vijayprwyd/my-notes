---
attachments: [Clipboard_2020-01-20-09-31-44.png, Clipboard_2020-01-20-09-31-52.png, Clipboard_2020-01-20-09-38-09.png, Clipboard_2020-01-23-08-50-20.png, Clipboard_2020-01-23-08-51-20.png, Clipboard_2020-01-23-08-53-39.png]
tags: [CSS]
title: Transition
created: '2020-01-20T03:55:12.886Z'
modified: '2020-01-23T03:23:40.772Z'
---

# Transition

`transition: <property> || <duration> || <timing-function> || <delay> `


## transition-property

width , height , transform , padding , margin etc

## transition-duration

Duration of the transition

## timing-function

Specifies the speed curve of the transition effect

* **ease** - specifies a transition effect with a slow start, then fast, then end slowly (this is default)
* **linear** - specifies a transition effect with the same speed from start to end
* **ease-in** - specifies a transition effect with a slow start
* **ease-out** - specifies a transition effect with a slow end
* **ease-in-out** - specifies a transition effect with a slow start and end
* **cubic-bezier(x1,y1,x2,y2)** - lets you define your own values in a cubic-bezier function


## transition-delay

Specifies a Delay for the transition effect


## Transition + Transformation

```css

div {
  width: 100px;
  height: 100px;
  background: red;
  transition: width 2s, height 2s, transform 2s;
}

div:hover {
  width: 200px;
  height: 200px;
  transform: rotate(180deg);
}

```
![](@attachment/Clipboard_2020-01-20-09-38-09.png)

![](@attachment/Clipboard_2020-01-23-08-53-39.png)

