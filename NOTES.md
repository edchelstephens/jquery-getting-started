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