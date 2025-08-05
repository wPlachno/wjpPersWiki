# AlpineJS

AlpineJS is a small open source tool for Javascript which reformats some smaller common logic (think adding data into an html element, then using that data to control the other html attributes, also known as "State") and makes it easier to do responsive html without always poking at the DOM.

## State and HTML

In pure HTML, your inputs can be given a class name, and your javascript can access the DOM and use your class name to get the HTML element, then access the value.

In Alpine and other stateful tools, the value is given a name of its own and used without having to hit the DOM. 

### Alpine and State

Alpine uses some [new HTML element attributes](https://alpinejs.dev/) to [implement state](https://alpinejs.dev/start-here). The `x-data` attribute can store some data, `x-on:click`, which has a shorthand `@click`, can act as an event handler, and `x-text` can bind the `innerText` to the data in `x-data`. You can also use `x-show` to bind the visibility of an element to some `x-data`. Similar to `x-text`, `x-model` binds a data property to the value of an element.

## Alpine UI Components

While Alpine is open source, users can purchase a [separate library](https://alpinejs.dev/components) of copy-and-paste components built by the Alpine developers. This is the money they use to maintain Alpine. These components include Dropdowns, Modals, Accordions, Tabs, and many more. The library also includes integration code for pulling in third party tools like charts, text editors, calendars, and more. The current price, as of 11/8/23, is $129.