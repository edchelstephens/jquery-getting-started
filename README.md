# Jquery Getting Started

## From pluralsight course:

### [jQuery: Getting Started by Craig Shoemaker](https://app.pluralsight.com/library/courses/jquery-getting-started/table-of-contents)

# CSS3 Selectors

- selectors are strings that identify elements on an html page

## Id selector

- Values for id must be unique on a page

  `<div id="my-div"></div>`

- id is "my-div"
- to select with jquery use `#` prefix, e.g. `#<id>` --> `$("#my-div")`

## Class selector

- Values for class can be repeated and have multiple space-separated values
  `<div class="col-3"></div>`
  `<div class="col-3"></div>`
  `<div class="col-3"></div>`

- to select with jquery use `.` prefix, e.g. `.<class>` --> `$(".col-3")`

## Pseduo class

- Pseudo class reflect a specific state of an element

```
<html>
    <head>
        <style>
            a:hover { background-color: green; }
        </style>
    </head>
    <body>
        <div id="content-container>
            <h1 class="title">Intro</h1>
            <p>
                <a>Hover me green </a>
            </p>
        </div>

    </body>
</html>
```

- To get the first element of the div we say: `$("div:first-child")`
