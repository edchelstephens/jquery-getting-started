# Notes

# The jQuery library is actually declared in a variable `jQuery` as a function

# The `$` sign

- the `$` sign is just an alias to jQuery function
- The code below are the same:

```
    $(function(){
        console.log("Hi jquery");
    })
```

```
    jQuery(funciton(){
        console.log("Hi jquery");
    })
```

## Essentailly `$ = jQuery`

### jQuery and $ is an alias to the jQuery function

- saying $(); executes the jQuery function

# The jQuery ready function:

```
$(function(){

})
```

- this is the saying that after the page has loaded, "ready", execute whatever is inside the anonymous function called in jquery function

- the above is the same as:

```
jQuery(function(){
    // setup after page is ready

})
```

# When jQuery "queries" a page, or selects something in a page, it actually retuns a set or an array of those items - which is called a `wrapped set`

# let divs = $("div")

- this will return all the divs on the page

# let h2s = $("h2")

- this will return all the h2's on the page

## Even if there's only 1 div or 1 h2 on the page, you're going to get back a set always, the `wrapped set` value, that is, a set of 1 item in this case.

## Executing a funciton like `.addClassName` to a single set item and a multiple set, wrapped set, the action is the same, it applies to all the elements

## When querying something that does not exists, jQuery just simply returns an empty wrapped set.

# jQuery works in sets, e.g. the `wrapped set`

# jQuery also has this notion of getter and selector functions on wrapped set

## query:

    let h2 = $("h2")

### getter:

    h2.text() -> this returns the h2 text
    h2.text('new text') -> this sets the text of h2 to 'new text'

# HTML Literals

- by passing a a fragment of html in jquery, you can create html elements in memory
  `$("<div>This is a div</div>")`
- creates a div element in memory

- You can also create an array of elements with:

`let elements = $(['<span>one</span>', '<b>bold</b>', '<strong>strong</strong>'])`

# Parents and Children

- You can also get the parents and children of an html element with

`$(<query_selector>).parents(<parent_query_selector>)`
and

`$(<query_selector>).children(<children_query_selector>)`

# The `attr` function

- Function to manipulate just about any attribute on an element

`$("h2").attr("style", "color:red")`
This query changes the style of all h2s with color red.

# The `css` function

- the `css` funciton is a getter/setter function on a particular css style attribute of an element

e.g.:

##### getting the background color with css:

`$("h2").css("background-color")`

> > > 'rgba(0, 0, 0, 0)'

or with javascript
`$("h2").css("backgroundColor")`

> > > 'rgba(0, 0, 0, 0)'

##### setting the background color:

- you actually pass a javascript object with css styles on camelCase because this is javascript not css
  `$("h2").css({backgroundColor:"red"})`
  and querying again
  `$("h2").css("background-color")`
  > > > 'rgb(255, 0, 0)'

### addClass() and removeClass() functions

- adds or removes css class on element
  `$("h2").addClass("highlight")`
  `$("h2").removeClass("highlight")`

- you can also pass a callable on addClass and removeClass that returns the string of css class to add or remove

`let len = 1`

`$("h2").addClass(()=>{

    return  len == 1 ? "highlight":"bordered"

})`

`$("h2").removeClass(()=>{ return len < 0 ? "highlight bordered": "bordered" })`

# hide() and show() functions

- hides or shows an element by setting the display property
  `$("h2").hide()`
  `$("h2").show()`

# toggle()

- toggles hide or show
  `$("h2").toggle()` -> shows the h2s if they are hidden, or hides them if they are shown

## hide(), show() and toggle() can also take callables which are things you can perform when on the action, like showing a notification toaster on toggle, etc

`$("h2").toggle(()=> { toastr.success(message="Feature hidden")})`

### fadeIn(), fadeOut()

- fades in or out the selected wrapped set

- you can also pass a callable on these functions to perform actions after fadeIn or fadeOUt
  `$("h2").fadeIn(()=>{ $("#special-features").addClass("bordered")})`
  this adds `bordered` class on element with id `special-features` after the h2's are done fading in

# Events

- just an event, that happens and then you can listen to them and do some actions

Example HTML events:

1. Page Load
2. Key Pressed
3. Button Clicked
4. Form Submitted
5. Window Scrolled
6. Element Focused

# The jQuery read() function

- runs when the page has been loaded completely and ready to be manipulated with scripts

syntax:
`$(document).ready(()=>{ // things to do here })`

shortcut:
`$(()=>{ // things to do here })`

# The `on` function

- takes 2 paramenters,
- `on(eventName, callable)`
- example:
  `$("#save-button").on("click", ()=>{ console.log("save button clicked") })`

# The `off` function

- `off(event)`
- Stop listening to the event on the object
- example, stop listening on on click events:
  `$("#save-button").off("click")`

# The `one` function

- `one(eventName, callback)`
- executes the callback on the first occurence of the event only
  example:
  `$("#save-button").one("click", ()=>{ console.warn("One click only")})`

  # The `click` function

  - `click(callback)`
  - executes the callback on click events on the element
  - this is a shorcut to `on("click", callback)`
    example:
    `$("#save-button").click(()=>{ console.warn("save button clicked")})`

# More event functions here:

https://api.jquery.com/category/events/

examples:
the `dblclick(callBack)` function:
`$("#save-button").dblclick(()=>{ console.error("double clicked")})`

the `mouseenter(callback)` function:
`$("#save-button").mouseenter(()=>{ console.error("mouse enter")})`

the `blur(callback)` function

- `$("#save-button").blur(()=>console.warn("blurrinng, don't blur"))`

# HTML events reference here:

https://developer.mozilla.org/en-US/docs/Web/Events

# jQuery chaining

instead of this approach which queries the div elements 3 times:
`$("div").addClass("bordered")`
`$("div").height("200px")`
`$("div").width("50%")`

you can just apply one query with chaning:
`$("div").addClass("bordered").height("200px").width("50%")`
This way it's more efficient since the element query or selection only happens once they just the styles get's applied via chaining

# since jquery returns a wrapped set, you can perform set operations with it like `each` https://api.jquery.com/each/

```
let items = $("#special-features li");

items.width("50%")
        .height("200px")
        .addClass("highlight bordered")
        .each((index, item)=>{
          console.warn("index:", index)
          console.error("item:", item)
          let $item = $(item);
          let item_text = $item.text()
          console.log("item text:", item_text)
          item_text = item_text + " with id -> " + $item.attr("data-feature-id")
          console.warn("updated item text:", item_text)
          $item.text(item_text)
                  })
```

Chaining applies to all items of the wrapped set, even if just one.

```
let saveButton = $("#save-button");

saveButton.click(()=>{

    console.warn("About to be bordered")
}).addClass("bordered")

```
