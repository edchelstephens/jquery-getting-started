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
