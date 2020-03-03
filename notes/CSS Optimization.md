---
attachments: [Clipboard_2020-02-03-10-05-19.png]
tags: [Web Performance]
title: CSS Optimization
created: '2020-02-03T03:56:54.265Z'
modified: '2020-02-10T06:25:12.437Z'
---

# CSS Optimization


### 1. **Minification**

### 2. **Use shorthand CSS** for properties like margin, padding, border etc whereever applicable

```css

  margin: margin-top, margin-right, margin-bottom, and margin-left

  margin: 10px /* All sides 10px */
  margin : 10px 20px // top, bottom = 10px,  left. right = 20px
  margin: 10px 20px 30px // top = 10px, bottom = 30px, left/right = 20px

```

### 3. **Use shallow CSS selectors**

* Overly specific selectors that are many levels deep may be replaced by shallow selectors

  ```css

  div.mainContent div.genricList {} 

  .genericList {} // Shalloe selector

  ```

### 4. Avoid nesting when using CSS precompilers like Less or Sass 

* Nesting makes the selectors too specific.
* Overly specific selectors can increase file size and slow rendering time as well

```css

// Sass

.abc {
  margin-top: 20px;
  .xyz {   
      margin-top:10px;
  } 
}


// compiled to 

.abc {
	 margin-top: 20px;
}
 .abc .xyz {    // All xyz that are descendants of abc
	 margin-top: 10px;
}

```

### 5. Avoid CSS duplication

Avoid multiple selectors that specify same background or font style


```css

// Avoid css redundancies

#main {
  background-color: white;
}

#section {
  background-color: white
}

// After removing redundancy

#main, #side {
  background-color: white
}

```

### 6. Segment CSS

* Segmentation splitS CSS by styles specific to particular page templates
* Prevents users from downloading css files they never see


![](@attachment/Clipboard_2020-02-03-10-05-19.png)


### 7. Placing CSS at the head of html

* Users can see flash of unstyled content

* Avoid re-render and repaint the entire DOM

* Progressive Rendering : Render content for display as quickly as possible

* CSS is render blocking

### 8. Avoid @import serialize requests

### 9. <link> paralleize request

### 10. Using faster selectors

 * The sibling, pseudo class, and attribute selector types are especially expensive.
