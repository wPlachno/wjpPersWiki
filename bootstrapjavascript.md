# Bootstrap Javascript

## Save Some Memory

Some Bootstrap solutions may choose to not include the [Popper](popperjs.md) or the Bootstrap Javascript, usually to decrease page load times. The CSS is still linked and includes most of the Bootstrap functionality, but according to [Bootstrap Documentation](https://getbootstrap.com/docs/5.3/getting-started/introduction/#js-components), removing the Javascript files will reduce functionality:

| Component | No PopperJS | No BootstrapJS |
| --- | --- | --- |
| Alerts for dismissing | Pass | Fail |
| Buttons for toggling states and checkbox/radio functionality | Pass | Fail |
| Carousel for all slide behaviors, controls, and indicators | Pass | Fail |
| Collapse for toggling visibility of content | Pass | Fail |
| Dropdowns for displaying and positioning | Fail | Fail |
| Modals for displaying, positioning, and scroll behavior | Pass | Fail |
| Navbar for extending Collapse and Offcanvas plugins | Pass | Fail |
| Navs with the Tab plugin for toggling content panes | Pass | Fail |
| Offcanvases for displaying, positioning, and scroll behavior | Pass | Fail |
| Scrollspy for scroll behavior and navigation updates | Pass | Fail |
| Toasts for displaying and dismissing | Pass | Fail |
| Tooltips and popovers for displaying and positioning | Fail | Fail |

If including both, you should use the bundle: 

`<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/js/bootstrap.bundle.min.js" integrity="sha384-C6RzsynM9kWDrMNeT87bh95OGNyZPhcTNXj1NW7RuBCsyN/o0jlpcV8Qyq46cDfL" crossorigin="anonymous"></script>`

You can separate them out into: 

`<script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.11.8/dist/umd/popper.min.js" integrity="sha384-I7E8VVD/ismYTF4hNIPjVp/Zjvgyol6VFvRkX/vR+Vc4jQkC+hVqc2pM8ODewa9r" crossorigin="anonymous"></script>`

`<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/js/bootstrap.min.js" integrity="sha384-BBtl+eGJRgqQAUMxJ7pMwbEyER4l1g+O15P+16Ep7Q9Q+zqX6gSbd85u4mG4QzX+" crossorigin="anonymous"></script>`

Or, remove them as necessary.

## Compatible Frameworks

The Bootstrap css files are just that and can be dropped into most modern web frameworks, but the javascript files have issues when combined with React, Vue, or Angular. The workaround is to use a [different Bootstrap javascript file](https://getbootstrap.com/docs/5.3/getting-started/javascript/#usage-with-javascript-frameworks) tailored to whichever framework you are using.