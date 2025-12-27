# HTML Pages and Elements

The presentaiton form of the web is using HTML and CSS. We will be exploring HTML in this lesson to understand how to structure it, utilise its attributes and event system.

## Elements and Tags

HTML elements are markup text in which usually have an opening and closing tag. A tag is denoted with a `<` and `>` in which a closing tag is denoted with `</` and `>`. Occasionally some tags may include *self close*, although this is more of an oddity/legacy thing that is still debated to this day.

To demonstrate how tags functions, we will create a **paragraph** element using the following tags.

For example, the opening tag for `<p>` has the closing tag `</p>`.

```html
<p>
  The content for the paragraph goes here
</p> 
```

While HTML does not officially have *self-closing tags*, you will occasionally see `<img />` and `<br />` utilise them, however they are considered unnecessary as part the HTML specification as the element itself is usually acknowledged to not have content inbetween so `<img >` and `<br>` are completely acceptable.

## Structuring

Within HTML, there are different kinds of structures that you will need to acknowledge and memorise to be as efficient as possible.

A HTML document will contain the following elements normally all the time. We will look into a simple scaffold on the next for HTML and explain it.


```html
<!DOCTYPE html>
<html>
  <head> <!-- Head Element starts  -->
  
    <title> <!-- Title Tag, opening -->
      My first website!
    </title> <!-- Title ends here -->
    <meta charset="utf-8" />

  </head> <!-- Head Element ends here -->
  
  <body> <!-- What would be displayed in the browser -->
    <article>
      <header> <!-- Header of the article -->
        A day in the life
      </header>
      <section> <!-- Body of the article -->
        I read the news today, oh boy! 
      </section>
    </article>
  </body>
</html>
```

The above snippet is fairly typical, particularly the following elements `<html>`,
`<head>`, `<title>`, `<meta>` and `<body>` as these are typically all required for displaying and setting the necessary components of a page.

## Attributes

HTML elements have attributes, while they are as heavily used as they were once. They are still important when associating with styles or providing data that can be used.

The kind of attributes we have available with our DOM elements are.

* Standard Attributes
* Event Attributes
* Data Attributes
* ARIA Attributes

### Standard Attributes

The standard attributes are ones which apply to all elements (almost). These can include `id`, `class`, `style`, `title`, `lang` and `dir`.

Most of the time, the `id`, `class` and `style` attributes are utilised as they serve the purpose most useful for styling.


### Data Attributes

An important set of attributes are `data-*` attributes or known as **data-attributes**. Data attributes are able to describe and encode data.

```html
  <article
    id="electric-cars"
    data-columns="3"
    data-index-number="12314"
    data-parent="cars">
    <!-- Electric car content -->
  </article>

  <article
    id="solar-cars"
    data-columns="3"
    data-index-number="12315"
    data-parent="cars">
    <!-- Solar car content -->
  </article>

  <article
    id="flying-cars"
    data-columns="4"
    data-index-number="12316"
    data-parent="cars">
    <!-- Flying car content -->
  </article>
  
```

Within javascript, these elements can be queried and their data extracted.


### Event Attributes

Elements in the DOM, have event attribute, not all DOM elements will be able to work nicely with certain events but one can try.

Common event types can include `onclick`, `onkeypress`, `onchange` and `onfocus`.

These attributes are usually being associated with a **Javascript Function** that they will trigger when interacted with.

```html
<button onclick="sendResponse()">
Send
</button>
```

The above snippet shows the `onclick` attribute being set to a string that looks like a function call. This string is eventually **evaluated** and interpreted as javascript and can be executed.


### ARIA Attributes

Accessibility is very important in the web. To help with describing a particular object which may not necessarily be displayed as text, `aria-*` attributes assist with describing the them via `aria-label` but also by giving information about its current state and status.

Consider the scenario where we have a halloween themed website. We use language like `Run Away` to describe exiting the website or moving to another screen.

```html
<button aria-label="Exit">
  Run away
</button>  
```

It may not be necessarily clear for someone what `Run Away` is doing, especially if they are vision impaired. However the `aria-label` serves the purpose of revealing the true intent is.

For other attributes, consider the following as `aria-label` should be the be-all and end-all of accessibility.

* `aria-role` - Used to describe the role the element is taking such as toolbar, cell or document.

* `aria-describedby` - It refers to the an id of another element which contains the description

* `aria-description` - Similar to describedby but has the description associated.
