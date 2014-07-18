# ![appear](https://raw.githubusercontent.com/creativelive/appear/master/assets/appear-64.png) appear

Track the visibility of dom elements and fire user defined callbacks as they appear and disappear from view.

## Usage

Include appear.js in your page, it has no dependencies.

Call `appear()` passing in an object with the following:

- `init` function to run when dom is interactive, but before appear.js has started tracking.
- `elements` *required* function that returns an htmlcollection of elements to track. The dom will be interactive at this point. Can alternatively be an existing htmlcollection instead of a function.
- `appear` function to run when an element is in view, passed the element that has come into view. If defined then appear.js will track elements until they come into view.
- `disappear` function to run when an element goes out of view, passed the element that has gone out of view. If defined then appear.js will track elements until they go out of view.
- `reappear` if true appear.js will keep tracking elements for successfuive appears and dissappears. Default is false.
- `bounds` increase, in pixels, to the threshold size of the element so it can be "viewable" before it is actually in the viewport.
- `debounce` appear.js tracks elements on browser scroll and resize, for performance reasons this check is "debounced" to only happen once for multiple events, 50ms after the last event ends. You can override this value here.
- `deltaSpeed` in addition to debouncing, appear.js will also check for items during continuous slow scrolling, you can controll how slow the scrolling should be via this value. Default is 50 (pixels).
- `deltaTimeout` after a succesful delta speed check, appear.js will not check for viewable items again until this timeout passes. Default is 500 (ms).
- `done` function called when appear.js is no longer tracking any items and event listeners have been removed.

## Example

```javascript
appear({
  init: function init(){
    console.log('starting');
  },
  elements: function elements(){
    // for example, get all elements with the class "lazy"
    return document.getElementsByClassName('lazy');
  },
  appear: function appear(el){
    console.log('visible', el);
  },
  disappear: function disappear(el){
    console.log('no longer visible', el);
  },
  reappear: true
});
```

View `test/index.html` in a browser for more example usage.

`appear()` will return an object with the following:

- `elements` the array of elements the appear instance is tracking.
- `trigger()` force a check for viewable elements.
- `pause()` stop tracking elements.
- `resume()` resume tracking elements.
- `destroy()` destroy the appear instance, permanently stop tracking elements.


## Download

[source](https://github.com/creativelive/appear/blob/master/dist/appear.js) or [minified](https://github.com/creativelive/appear/blob/master/dist/appear.min.js)

---

appear.js logo designed by [Magicon](http://thenounproject.com/magicon) from the [Noun Project](http://thenounproject.com/) :: Creative Commons - Attribution (CC BY 3.0)
