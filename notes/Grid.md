---
attachments: [Clipboard_2020-01-19-21-16-06.png, Clipboard_2020-01-19-21-25-49.png, Clipboard_2020-01-19-21-27-08.png, Clipboard_2020-01-19-22-35-33.png, Clipboard_2020-01-20-11-26-58.png, Clipboard_2020-01-20-17-57-13.png, Clipboard_2020-01-20-18-03-49.png, Clipboard_2020-01-20-18-14-34.png, Clipboard_2020-02-02-21-10-49.png, Clipboard_2020-02-02-22-42-04.png]
tags: [CSS]
title: Grid
created: '2020-01-19T15:37:03.854Z'
modified: '2020-02-02T17:26:26.847Z'
---

# Grid

* Grid based layout system with rows and columns
* The vertical lines of grid items are called columns.
* The horizontal lines of grid items are called rows.


Properties :

**Grid Gaps** ( grid-column-gap, grid-row-gap , grid-gap)
**Grid Lines** (grid-row-start, grid-row-end , grid-column-start, grid-column-end)
**grid-template-columns**
**grid-template-rows**
**justify-content** ( space-evenly, space-around, space-between)
**align-content** ( )


## 1.Grid gaps

* grid-column-gap
* grid-row-gap
* grid-gap ( grid-column-gap grid-row-gap)

The spaces between each column/row are called gaps.

```css

.grid-container {
  display: grid;
  grid-template-columns: auto auto auto auto;
  background-color: #2196F3;
}

.grid-item {
  background-color: rgba(255, 255, 255, 0.8);
  border: 1px solid rgba(0, 0, 0, 0.8);
  padding: 20px;
  font-size: 30px;
  text-align: center;
}

```
```html

<div class="grid-container">
  <div class="grid-item">1</div>
  <div class="grid-item">2</div>
  <div class="grid-item">3</div>  
  <div class="grid-item">4</div>
  <div class="grid-item">5</div>
  <div class="grid-item">6</div>  
  <div class="grid-item">7</div>
  <div class="grid-item">8</div>
  <div class="grid-item">9</div>  
</div>


```


![](@attachment/Clipboard_2020-01-19-21-16-06.png)

### grid-row-gap

* sets the gap between the rows

```css
.grid-container {
  display: grid;
  grid-row-gap: 50px;
  grid-template-columns: auto auto auto;
}
```

![](@attachment/Clipboard_2020-01-19-21-25-49.png)

### grid-column-gap

* sets the gap between the columns


```css

.grid-container {
  display: grid;
  grid-column-gap: 50px;
  grid-template-columns: auto auto auto;
}

```

![](@attachment/Clipboard_2020-01-19-21-27-08.png)

### grid-gap

The grid-gap property is a shorthand property for the grid-column-gap and the grid-row-gap properties

## 2. Grid Lines

      *  Column lines: The lines between columns are called column lines.

      * Row lines: The lines between rows are called row lines.

![](@attachment/Clipboard_2020-01-20-11-26-58.png)


**Row lines**


```css

.grid-container {
  display: grid;
  grid-template-columns: auto auto auto;
  grid-gap: 10px;
}

.item1 {
  grid-row-start: 1;
  grid-row-end: 3;
}

```


![](@attachment/Clipboard_2020-01-20-17-57-13.png)


**Column Lines**

```css

.grid-container {
  display: grid;
  grid-template-columns: auto auto auto;
  grid-gap: 10px;
}

.item1 {
  grid-column-start: 1;
  grid-column-end: 3;
}

```

![](@attachment/Clipboard_2020-01-20-18-03-49.png)

### 3. grid-template-columns

* defines the number of columns in the grid layout, and it can define the width of each column.

```css

.grid-container {
  display: grid;
  grid-template-columns: 80px 200px auto 30px;
  grid-gap: 10px;
}

.grid-container > div {
  padding: 20px 0;
  font-size: 30px;
}

```

![](@attachment/Clipboard_2020-01-20-18-14-34.png)




### 4. grid-template-rows

* defines the height of each row


```css

.grid-container {
  display: grid;
  grid-template-rows: 80px 200px;
}

```

![](@attachment/Clipboard_2020-02-02-21-10-49.png)

### 5.justify-content


```css

.grid-container {
  display: grid;
  justify-content: start;
}

```


* Horizontally align the whole grid inside the container

![](@attachment/Clipboard_2020-02-02-22-42-04.png)

### 6. align-content




