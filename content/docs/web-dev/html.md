---
type: "docs"
title: HTML
draft: false
---

# HTML

**HTML** - Hyper Text Markup Language

**Tags and Elements**

```html
<p>some text content</p>
<!-- Tag -->
```

## <a>

**Reserved Characters, Quotes & Other Escape Characters**

| Character | Escape Syntax |
| :-------: | :-----------: |
|    `<`    |     `&lt`     |
|    `>`    |     `&gt`     |
|    `&`    |    `&amp`     |
|    `'`    |   `&rsquo;`   |
|    `"`    |   `&ldquo;`   |
|    `"`    |   `&rdquo;`   |
|    `‘`    |   `&lsquo;`   |

More characters [here](https://html.spec.whatwg.org/multipage/named-characters.html)

---

**Void Elements** - Some elements do not have a closing tag. These elements have only opening tag.**Eg :** `<br>`, `<img>` etc. Some elements just have a forward slash at the end like : `<br />` or `<img />`. The latest version of HTML specification specifically discourages their use and considers them invalid.

**DOCTYPE** - Every HTML page starts with a doc type declaration. DOCTYPE's purpose is to tell the browser what version of HTML it should use to render the document. The latest version is HTML5, and the doctype for that version is simply `<!DOCTYPE html>`

The doctypes for older versions of HTML were a bit more complicated. For example, this is the doctype declaration for HTML4:
`<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">`

**HTML Element** - We need to provide an `<html>` element. This is the root of the document, meaning every other document descends from it.

```html
<!DOCTYPE html>
<html lang="en"></html>
```

**Head Element** - The `<head>` element is where we put important meta-info about our webpages, and stuff required for our webpages to render correctly in the browser. Inside the `<head>`, we should not use any element that displays content on the webpage.

**Meta Element** - We should have the `<meta>` tag with the charset encoding of the webpage in the `<head>` element : `<meta charset='utf-8`

**Title** - The `<title>` element is used to give webpages a human-readable title which is displayed in our webpage's browser tab.

**Body Element** - The final element to complete the HTML boilerplate is the `<body>` element.This is where all the content that will be displayed to users will go - the text, images, lists, links and so on.

---

**Viewing the HTML files in the browser - New Way**

1. Ubuntu - Open terminal in the html file location, type `google-chrome index.html`
2. MacOS - In the directory, type `open./index.html`

**Commenting in HTML**

```html
<!-- I am a HTML comment -->
```

---

## Lists

### `<start>` Attribute

The `<start>` attribute defines the number from which an ordered list should start. By default, ordered lists start at 1.

```html
<ol start="30">
  <li>Head north on N Halsted St</li>
  <li>Turn right on W Diversey Pkwy</li>
  <li>Turn left on N Orchard St</li>
</ol>
```

### `<reversed>` Attribute

The `<reversed>` attribute is a Boolean attribute when used on the <ol> element, allows a list to appear in reverse order. An ordered list of five items numbered 1 to 5 may be reversed and ordered from 5 to 1.

```html
<ol reversed>
  <li>Head north on N Halsted St</li>
  <li>Turn right on W Diversey Pkwy</li>
  <li>Turn left on N Orchard St</li>
</ol>
```

### `<value>` Attribute

Used on an individual `<li>` list element within an ordered list to change its value eithin the list. The number of any list item appearing below a list item with a `<value>` attribute will be recalculated accordingly.

```html
<ol>
  <li>Head north on N Halsted St</li>
  <li value="9">Turn right on W Diversey Pkwy</li>
  <li>Turn left on N Orchard St</li>
</ol>
<!-- The list number changes to 9 and starts incrementing from there -->
>
```

- More kinds of lists and list attributes can be found @ [Shay Howe's Blog](https://learn.shayhowe.com/html-css/creating-lists/)

---

## Links and Images

### Opening Links in a New Tab

```html
<a
  href="https://www.theodinproject.com/about"
  target="_blank"
  rel="noopener noreferrer"
  >click me</a
>
```

- _target_ attribute specifies where the link source will be opened.
- By default it will take on the _\_self_ value which opens the link in the current tab. To open the link in a new tab or window set it to _\_blank_
- _rel_ attribute is used to describe the relation between the current page and the linked document.
- _noopener_ value prevents the opened link from gaining access to the webpage from which it was opened.
- _noreferrer_ value prevents the opened link from knowing which webpage or resource has a link to it. It also includes the _noopener_ behaviour and thus can be used by itself as well.

> The prevention of access that is caused by _noopener_ prevents **phishing** attacks where the opened link may change the original webpage to a different one to trick users. This is referred to as **tabnabbing**. Adding the _noreferrer_ value can be done if you wish to not let the opened link know that your webpage links to it.

### Absolute and Relative Links

- When including relative links, prepone the link with `./` to avoid unexpected issues if both the pages/content are in the same directory

### Images

- Image width and height can be adjusted within the `img` tag itself

```html
<img
  src="https://www.theodinproject.com/mstile-310x310.png"
  alt="The Odin Project Logo"
  height="310"
  width="310"
/>
```

- Image Formats that can be used in HTML :

  - JPG | GIF | PNG | SVG

## 7 Golden Rules for Git Commit

1. Separate the subject from body with a blank line

2. Limit the subject line to 50 characters

3. Capitalize the subject line

4. Do not end the subject line with a period

5. Use the imperative mood in the subject line

6. Wrap the body at 72 characters

7. Use the body to explain _what_ and _why_ vs _how_
