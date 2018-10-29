# onElementInteraction

Attaches a listener to an element which is fired when the element is _touched_ or _clicked_.

```javascript
const { remove } = Kiosked.API.onElementInteraction(
  document.querySelector(".myButton"),
  function() {
    console.log("Interaction detected!");
    // remove listener
    remove();
  }
);
```

_In this example, an element is fetched by the `querySelector` call and then watched by the `onElementInteraction` method. The callback function is fired once the button is activated. The callback also makes use of the returned `remove` method, which can be used to detach the listener.

The method has the following signature:

`onElementInteraction(element, callback [, throttle])`

| Parameter     | Type     | Required | Default   | Description               |
|---------------|----------|----------|-----------|---------------------------|
| element       | Element  | Yes      |           | A `HTMLElement` instance to listen on. |
| callback      | Function | Yes      |           | The function to execute when the element is activated. |
| throttle      | Number   | No       | 100       | Milliseconds to throttle the calls. If multiple calls occur within the throttle time, only the first will be received. |

The return value is an `Object` that contains the single property `remove`, which is a `Function`. Calling `remove` will immediately clear the listener so that it does not fire.
