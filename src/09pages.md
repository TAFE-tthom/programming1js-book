# Defining Pages and Content

As part of using the different tags with HTML, we need to know how to best combine the tags in which they are designed to be used.


## HTMl, Head and Body

A HTML document is composed of the `<!DOCTYPE html>`, `<html>`, `<head>` and `<body>` tags.

These form the description of the document version type that is being used. Where the HTML content tree effectively starts, the header of the document and lastly the body/content of the document.

```html
<!DOCTYPE html>
<html>
  <head>

    <!--- header --->

  </head>

  <body>

    <!--- content --->

  </body>
</html>  
```

Within the header, you will specify the `<title>`, `<meta>` as well as `<link>` and other relevant tags.


Within the body, you will specify majority of the other HTML tags that are used as part of displaying content.

These will include `<article>`, `<p>`, `<img>`, `<section>` and `<header>` (as well as many many more!).

Let's use the following.

```html
<head>
  <title>My First Web Page!</title>
  <meta charset="utf-8" />
</head>

<body>
  <article>
    <header>Bug Story!</header>
    <section>
      This is a story
      about a bug
      that had
      a very rainy day
    </section>
  </article>
</body>
```

The above snippet shows how the head tag will provide a title and outline the `charset` (character encoding) of the data.

The body contains an article with a header and a section which is the content of the article. You can kind of think of it like a newspaper.

## Elements

### Block and Inline Elements

There are two types of elements in which their defaults dictate their use-cases. Block level elements which will be displayed and considered their own object.
These include `<p>`, `<ul>` and `<div>`.

Contrasting this with **inline elements**, these are elements that are part of the content itself or as used to describe it.

These include `<b>`, `<br>` and `<code>`. While it possible to change they are styled and their representation, the defaults exist to provide some semantic meaning to the content and the element it is stored in.

### Common elements

You will usually fine `<p>` and `<div>` on most websites. `<p>` standing out for paragraphs and only expecting text data to be inside it. It is a block element which is expected to expand horizontally first.

```html
<p>


</p>  
```

`<div>` on the otherhand is a lot more versatile and takes on a generic container. It is used to create **division** or some distinction between elements.


### Lists

Lists come in different forms, commonly `<ul>` is used in conjunction with `<li>` to display entries.

```html
<ul>
  <li>Get Milk</li>
  <li>Get Bread</li>
  <li>Pay for groceries</li>
</ul>
```

However, `<dl>`, `<dt>` and `<dd>` are used to also describe a list. This is known as a description list. 

```html
<dl>
  <dt>Get Milk</dt>
  <dd>Should be $4.50</dd>
  <dt>Get Bread</dt>
  <dd>It is $3.25</dd>
  <dt>Pay for groceries</dt>
  <dd>Pay $7.75</dd>
</dl>
```

### Linking

It wouldn't be much of a website if we could link data inside it. To do so, you would use the anchor `<a>` tag.

You can do **internal linking** and **external linking**.

```html
<p>You may want to visit<p>

<ul>
  <li><a href="https://github.io/tafe-tthom/programming1js-book">Programming-1 Javasript</a></li>
  <li><a href="#Linking">This section</a></li>
</ul>
```

The two links in the segment above represent two different kins. The first is a typical anchor link, it will go to another website (which is **external linking**), the other is known as a **skip link** which performs **internal linking**.
