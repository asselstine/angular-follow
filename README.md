angular-follow
==============

AngularJS Directive that allows an element to become fixed when the page is scrolled.

Usage
-----

To make an element follow the scroll, add the attribute *angular-follow* to the element:

	<h3 angular-follow>This is the header</h3>

You can customise the point at which the element follows the scroll by adding the *follow-point* attribute with the number of pixels you wish to buffer the follow by: 

	<h3 angular-follow follow-point='100'>This is the header</h3>

Now the element will become fixed when the top of the viewport is within 100px of the element.

Manual Install
-------

Just include the JavaScript file after the angular library inclusion.

Bower Install
-------------

Add the dependency to your bower.json file:

```json
{
  "name": "myproject",
  "version": "0.0.0",
  "authors": [
    "Brendan Asselstine <brendan@skyrkt.com>"
  ],
  "dependencies": {
    "angular": "1.2.1",
    "angular-follow": "latest"
  },
  "resolutions": {
    "angular": "1.2.1"
  }
}
```

Or install using bower install

```bash
bower install angular-follow
```

Behavior
--------

The directive will bind a scroll listener to the window that checks to see if the window has scrolled passed the element's *follow point*.  If it has then:

1. The element's CSS 'position' is set to 'fixed' and the CSS 'top' is set to the value of the *follow point* directive attribute.
2. A clone of the element is created as a sibling whose visibility is hidden
3. The width of the (now) fixed element is set to the width as calculated by it's non-fixed getBoundingClientRect() width.

If the window has scrolled back above the element's follow point then the above is reversed; including restoring the old CSS 'position' and 'top' attributes and destroying the clone.

