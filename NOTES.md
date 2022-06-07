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
