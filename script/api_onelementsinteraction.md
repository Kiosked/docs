# onElementsInteraction

Attaches a listener to multiple elements which is called if any are activated by _touching_ or _clicking_. Calls [`Kiosked.API.onElementInteraction`](script/api_onelementinteraction.md) under the hood.

```javascript
const { remove } = Kiosked.API.onElementsInteraction(
  document.querySelectorAll(".prev, .next"),
  function() {
    console.log("Interaction detected on some button!");
    // remove listener
    remove();
  }
);
```

The `onElementsInteraction` can also take a query selector string:

```javascript
Kiosked.API.onElementsInteraction(".buttonClass, #button", () => {});
```

The method signature is as follows:

`onElementsInteraction(queryOrElements, callback [, throttle])`

| Parameter       | Type     | Required | Default   | Description               |
|-----------------|----------|----------|-----------|---------------------------|
| queryOrElements | String / Array | Yes |          | An array of `HTMLElement`s or a CSS query selector string. |
| callback        | Function | Yes      |           | The function to execute when the elements are activated. |
| throttle        | Number   | No       | 100       | Milliseconds to throttle the calls. If multiple calls occur within the throttle time, only the first will be received. |

The return value is an `Object` that contains the single property `remove`, which is a `Function`. Calling `remove` will immediately clear the listener so that it does not fire.
