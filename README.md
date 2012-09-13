# Pragmatic.js code style guidelines

* `function name() { }` for named functions
* `function(){ }` for anonymous functions
* Use short and concise expressions
* Prefer functional programming over for or while loops
* No curly braces for single-line control flow statements such as `if` & friends
* Don't write [semicolons that are optional][optional]
* Put a single semicolon _before_ statements that start with `(` or `[`
  (see above article as for why it's needed)
* Use long, descriptive variable and method names
* Use blank lines to separate "paragraphs" of code for readability
* Use comments to describe non-obvious code behavior

### Examples

Here are some examples from [Zepto.js][zepto].

```
// typical helper function
function eachEvent(events, fn, iterator){
  if ($.isObject(events)) $.each(events, iterator)
  else events.split(/\s/).forEach(function(type){ iterator(type, fn) })
}

// shortcut methods for `.bind(event, fn)` for each event type
;('focusin focusout load resize scroll unload click dblclick '+
'mousedown mouseup mousemove mouseover mouseout '+
'change select keydown keypress keyup error').split(' ').forEach(function(event) {
  $.fn[event] = function(callback){ return this.bind(event, callback) }
})

// from Zepto core, $.fn.siblings implementation
function filtered(nodes, selector) {
  return selector === undefined ? $(nodes) : $(nodes).filter(selector)}
}

$.fn.siblings = function(selector){
  return filtered(this.map(function(i, el){
    return slice.call(el.parentNode.children).filter(function(child){ return child!==el })
  }), selector)
}
```

  [optional]: http://mislav.uniqpath.com/2010/05/semicolons/
  [zepto]: http://zeptojs.com/