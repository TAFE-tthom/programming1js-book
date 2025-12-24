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

\newpage

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

