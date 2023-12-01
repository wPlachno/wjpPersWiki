# BootstrapJS

Bootstrap is a Javascript and CSS library to allow a developer writing HTML to describe the style of an HTML element inside the class attribute instead of the style attribute. Bootstrap consistss of javascript and css files that you must include from the html.

## Installation

SCSS and Javascript are compiled into a library that must either be built into the server or attached as a link. If using the links, I suggest using the tags similar to the [very first guide](https://getbootstrap.com/docs/5.3/getting-started/introduction/) on the official site, particularly if you plan on using dropdowns or tooltips: 

```
<!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>Bootstrap demo</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-T3c6CoIi6uLrA9TneNEoa7RxnatzjcDSCmG1MXxSR1GAsXEV/Dwwykc2MPK8M2HN" crossorigin="anonymous">
  </head>
  <body>
    <h1>Hello, world!</h1>
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/js/bootstrap.bundle.min.js" integrity="sha384-C6RzsynM9kWDrMNeT87bh95OGNyZPhcTNXj1NW7RuBCsyN/o0jlpcV8Qyq46cDfL" crossorigin="anonymous"></script>
  </body>
</html>
```

If, however, you want to decrease page load, you could [try looking at whether you need the javascript files](bootstrap-javascript.md).

If you would prefer to use bootstrap as a module, you can follow [this guide](https://getbootstrap.com/docs/5.3/getting-started/javascript/#using-bootstrap-as-a-module).

## Bootstrap Usage Notes

To use Bootstrap on your page, you must include a proper HTML doctype and define the viewport, as correctly done above.

If you see some sizing issues when using third party software in the page, it may be because of Bootstrap redefining the `box-size` to `border-box` instead of the default `content-box`. Try setting `box-sizing: content-box;`

## Bootstrap Functionality

Bootstrap has many different modules, each with their own advantage.

| Type | Example | 
| --- | --- | 
| [CSS Customization](https://getbootstrap.com/docs/5.3/customize/overview/) | 
[Color Schemes](https://getbootstrap.com/docs/5.3/customize/color/), 
[Light/Dark mode](https://getbootstrap.com/docs/5.3/customize/color-modes/), 
[Base and Variation Classes](https://getbootstrap.com/docs/5.3/customize/components/) |
| Layout | 
[Breakpoints](https://getbootstrap.com/docs/5.3/layout/breakpoints/), 
[Containers](https://getbootstrap.com/docs/5.3/layout/containers/), 
the [Grid System](https://getbootstrap.com/docs/5.3/layout/grid/) |
| Content | 
[Typography](https://getbootstrap.com/docs/5.3/content/typography/), 
[Responsive Images](https://getbootstrap.com/docs/5.3/content/images/), 
[General Figures](https://getbootstrap.com/docs/5.3/content/figures/) |
| Components |
[Form Components](https://getbootstrap.com/docs/5.3/forms/overview/),
[Alerts](https://getbootstrap.com/docs/5.3/components/alerts/),
[Popovers](https://getbootstrap.com/docs/5.3/components/popovers/),
[Cards](https://getbootstrap.com/docs/5.3/components/card/),
[Scrollspy](https://getbootstrap.com/docs/5.3/components/scrollspy/) |
| Helpers |
[Ratio](https://getbootstrap.com/docs/5.3/helpers/ratio/),
[Contrasting Colors](https://getbootstrap.com/docs/5.3/helpers/color-background/),
[Text Truncation](https://getbootstrap.com/docs/5.3/helpers/text-truncation/) |