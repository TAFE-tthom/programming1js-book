# HTML Forms and Data

Forms within HTML are a commonly overlooked element. They provide a necessary function that also structures input for users. This input, once completed is likely to be sent to the server for processing and validation.

We'll analyse the form below:

```html
<form action="/newsletter" method="get"> <!-- Starting tag -->
  <div class="form-example">
    <!-- Label and Input have `for` and `name` attributes -->
    <!-- that match the same identifiers -->
    <label for="name">Enter your name: </label>
    <input type="text" name="name" id="name" required />
  </div>
  <div class="form-example">
    <label for="email">Enter your email: </label>
    <input type="email" name="email" id="email" required />
  </div>
  <div class="form-example">
    <!-- input is type `submit` which is a button -->
    <!-- but will use the url in `action` -->
    <input type="submit" value="Subscribe!" />
  </div>
</form> <!-- End tag -->
```

* Input and Label types are paired
* When submitting a form, `submit` input type is used instead of `button`
* `action` attribute will send form data inputted into fields with
  a `name` association with them to `/newsletter`


You'll have noticed the `<form>` tag has the attribute `method` which is typically `get` or `post`. Earlier, the form would usually send data as a query string using `get` or as part of a form body using `post`. We use more than the `get` and `post` these days with our HTTP requests but they are still used heavily.

