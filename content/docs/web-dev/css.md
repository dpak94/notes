---
type: "docs"
title: CSS
author: "dpak94"
draft: false
---

# CSS Notes

## Basic Syntax

![](https://cdn.statically.io/gh/TheOdinProject/curriculum/05ce472eabf8e04eeb2cc9139e66db884074fd7d/foundations/html_css/css-foundations/imgs/00.jpg)

## Selectors

**Selectors** simply refer to the HTML elements to which CSS rules apply - they are what is actually being _selected_ for each rule.

**Universal Selector** will select elements of any type, hence the name "universal", and the syntax for it is a simple asterisk `*`. In the below example, every element would have the `color : purple` style applied to it.

**Type Selector** will select all elements of the given element type, and the syntax is just the name of the element.

**Class Selectors** will select all elements with the given class, which is just an attribute youplace on an HTML Element. Here's how you add a class to an HTML tag and select it in CSS.

```html
<div class="alert-text">Please agree to our terms of service.</div>
```

```css
.alert-text {
  color: red;
}
```

**ID Selectors** are similar to class selectors. They select an element with the given ID, which is another attribute you place on an HTML Element. The major difference between classes and IDs is that an element can only have one ID.

```html
<div id="title">My Awesome 90's Page</div>
```

```css
#title {
  background-color: red;
  /* Hash instead of period */
}
```

**Grouping Selector** If we have two groups of elements that share some of their style declarations :

```css
.read,
.unread {
  color: white;
  background-color: black;
}

.read {
  /* several unique declarations */
}

.unread {
  /* several unique declarations */
}
```

**Chaining Selectors** Another way to use selectors is to chain thema as a list without any separation.

```html
<div>
  <div class="subsection header">Latest Posts</div>
  <p class="subsection preview">This is where a preview for a post might go.</p>
</div>
```

```css
.subsection.header {
  color: red;
}

.subsection#preview {
  color: blue;
}
```

In general, you can’t chain more than one type selector since an element can’t be two different types at once.

---

**Combinators** allow us to combine multiple selectors differently than either grouping or chaining them, as they show a relationship between the selectors.

A **Descendant Combinator** will only cause elements that match the last selector to be selected if they also have an ancestor (parent, grandparent, etc.) that matches the previous selector.

```html
<!-- index.html -->

<div class="ancestor">
  <!-- A -->
  <div class="contents">
    <!-- B -->
    <div class="contents"><!-- C --></div>
  </div>
</div>

<div class="contents"></div>
<!-- D -->
```

```css
/* styles.css */

.ancestor .contents {
  /* some declarations */
}
```

This code affects only B and C but not D becasue it does not share the ancestor class "ancestor" with B and C.

There is no limit on how many combinators you can add to a rule, but too many combinators may result in confusion. Tread carefully.

**Image Height and Width** If you wanted to adjust the size of the image without causing it to lose its proportions, you would use a value of “auto” for the `height` property and adjust the `width` value

```css
img {
  height: auto;
  width: 500px;
}
```

It’s best to include both of these properties for `<img>` elements, even if you don’t plan on adjusting the values from the image file’s original ones. When these values aren’t included, if an image takes longer to load than the rest of the page contents, the image won’t take up any space on the page at first, but will suddenly cause a drastic shift of the other page contents once it does load in.

Explicitly stating a `height` and `width` prevents this from happening, as space will be “reserved” on the page and will just appear as a blank space until the image loads.

> Inline CSS will override the other two methods, which can cause unexpected results.

---

## Box Model

**Positioning** & **Layout** are the most important skills to be mastered.

**The Box Model**

1. Every single thing on a webpage is a rectangular box.

2. These boxes can have other boxes in them and can sit alongside one another.

`padding` - increases the space between the border of a box and the content of the box.

`margin` - increases the space between the borders of a box and the borders of adjacent boxes

`border` - adds space (even if it's only a pixel or two) between the margin and the padding

![pm&b](https://cdn.statically.io/gh/TheOdinProject/curriculum/main/foundations/html_css/css-foundations/the-box-model/imgs/box-model.png)

### Display Types

**Inline, Block & Flex** Using the `display` property, you can set various values for the display type.

### Display : block

- If `display: block`, then the box will break onto a new line. The `width` and `height` props are respected.

- `padding`, `margin` &` border` props willcause other elements to be pushed away from the box.

- If `width` is not specified, the box will extend in the inline directioon to fill the space available in its container. In most cases, the box will become as wide as its container, filling up 100% of the space available.

  **Eg :** Some HTML elements like `h1` and `p`, use `block` as their outer display type by default.

### Display : inline

- If a box has an outer display type of `inline`, then the box will not break onto a new line.

- The [`width`](https://developer.mozilla.org/en-US/docs/Web/CSS/width) and [`height`](https://developer.mozilla.org/en-US/docs/Web/CSS/height) properties will not apply.

- Top and bottom padding, margins, and borders will apply but will not cause other inline boxes to move away from the box.

- Left and right padding, margins, and borders will apply and will cause other inline boxes to move away from the box.

**Eg :** Some HTML elements, such as `<a>`, `<span>`, `<em>` and `<strong>` use `inline` as their outer display type by default.

### Display : inner display

- Boxes also have an `inner` display type, which dictates how elements inside that box are laid out.

- Block and inline layout is the default way things behave on the web. By default and without any other instruction, the elements inside a box are also laid out in **[normal flow](https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Normal_Flow)** and behave as block or inline boxes.

- You can change the inner display type for example by setting `display: flex;`. The element will still use the outer display type `block` but this changes the inner display type to `flex`. Any direct children of this box will become flex items and behave according to the [Flexbox](https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Flexbox) specification.

More info @ [Mozilla Docs](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/The_box_model)

### Tips

- Always use `box-sizing: border-box;` property in the **Universal Selector** so that the height and width properties applied to descending elements remain what they they are.
- An inline element cannot contain a block-level element!

**Resources**

1. [Scrim Interactive on inline and block](https://scrimba.com/scrim/co5024997a7e46c232d9abe55)

---

## Flex Box

Flexbox is a way to arrange items into rows or columns. These items will flex (i.e. grow or shrink) based on some simple rules that you can define.

- A **flex container** is any element that has `display: flex` on it. A flex item is any element that lives directly inside of a flex container.

![Flexbox-illustration](https://cdn.statically.io/gh/TheOdinProject/curriculum/8c0402439e1b0a9a156731bdab4ea64162688dab/foundations/html_css/flexbox/imgs/03.png)

- Any element can be both a flex container and a flex item. Said another way, you can also put `display: flex` on a flex item and then use flexbox to arrange its children.

![Flexbox-iluustration-2](https://cdn.statically.io/gh/TheOdinProject/curriculum/495704c6eb6bf33bc927534f231533a82b27b2ac/html_css/v2/foundations/flexbox/imgs/04.png)

![Flex Direction](https://internetingishard.netlify.app/flex-direction-axes-b30e85.d1bca75a.png)

![Flex Direction Types](https://internetingishard.netlify.app/flex-direction-reverse-532d8f.d1f2fbd3.png)

**Flex Order**
![Flex Order](https://internetingishard.netlify.app/flex-direction-vs-order-021cee.7a3e129a.png)

**Flexible Items**
![Flexible Items](https://internetingishard.netlify.app/flexible-items-cfe7a3.e3584961.png)

- Use `display: flex;` to create a flex container.
- Use `justify-content` to define the horizontal alignment of items.
- Use `align-items` to define the vertical alignment of items.
- Use `flex-direction` if you need columns instead of rows.
- Use the `row-reverse` or`column-reverse` values to flip item order.
- Use `order` to customize the order of individual elements.
- Use `align-self` to vertically align individual items.
- Use `flex` to create flexible boxes that can stretch and shrink.

**Flex Shorthand**

The **flex** declaration is actually a shorthand for 3 properties that you can set on a flex item.  
**Eg :** `flex` is actually shorthand for `flex-grow`, `flex-shrink` and `flex-basis`.

```css
div {
  flex: 1;
}
```

In the above screenshot, `flex:1` equates to `flex-grow: 1`, `flex-shrink: 1` and `flex-basis: 0`

### Growing & Shrinking

#### Flex-Grow

`flex-grow` expects a single number as its value, and that number is used as the flex-item’s “growth factor”. When we applied `flex: 1` to every `div` inside our container, we were telling every `div` to grow the same amount.

#### Flex-Shrink

`flex-shrink` is similar to `flex-grow`, but sets the “shrink factor” of a flex item. `flex-shrink` only ends up being applied if the size of all flex items is larger than their parent container. For example, if our 3 divs from above had a width declaration like: `width: 100px`, and **.flex-container** was smaller than 300px, our divs would have to shrink to fit.

#### Flex-Basis

`flex-basis` sets the initial size of a flex item, so any sort of flex-growing or flex-shrinking starts from that baseline size. The shorthand value defaults to `flex-basis: 0%`

> Authors are encouraged to control flexibility using the flex shorthand rather than with its longhand properties directly, as the shorthand correctly resets any unspecified components to accommodate common uses.

More on flex [here](https://developer.mozilla.org/en-US/docs/Web/CSS/flex)

---
