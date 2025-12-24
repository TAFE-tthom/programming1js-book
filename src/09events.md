# Javascript Event Handling

Events are attributes on html elements that allow a bit of javascript code (normally a function assigned to it) to be triggered. A common event that is assigned to elements is `onclick`.

Below is an example of this event being assigned.

```html
<button onclick="sendMessage()">Send</button>
```

When a user click's the button, the `sendMessage()` function is called. You've probably seen a button like this when using an email client and sending an email. 

The `onclick` event can be assigned to elements and these event attributes can be assigned by the javascript as well through `document.getElementById` or some other querying method.

You are encouraged to look into the following events:

* `keydown`, `keyup`, `keypress` - Keyboard events
* `pointerover`, `pointerdown`, `pointermove`, ... - Pointer events
* `play`, `pause`, `seek`, ... - Audio events as part of the Audio element


