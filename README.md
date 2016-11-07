# Farbtastic: jQuery color picker plug-in

Farbtastic is a  [jQuery](http://www.jquery.com/) plug-in that can add one or more color picker widgets into a page. Each widget is then linked to an existing element (e.g. a text field) and will update the element&#39;s value when a color is selected.

Farbtastic uses layered transparent PNGs to render a saturation/luminance gradient inside of a hue circle. No Flash or pixel-sized divs are used.

Farbtastic was written by  [Steven Wittens](http://www.acko.net/dev/farbtastic) and is licensed under the GPL.

**Basic Usage**
--------------------------------------

1. Include farbtastic.js and farbtastic.css in your HTML:

&lt;script type=&quot;text/javascript&quot; src=&quot;farbtastic.js&quot;&gt;&lt;/script&gt;
&lt;link rel=&quot;stylesheet&quot; href=&quot;farbtastic.css&quot; type=&quot;text/css&quot; /&gt;

1. Add a placeholder div and a text field to your HTML, and give each an ID:

&lt;form&gt;&lt;input type=&quot;text&quot; id=&quot;color&quot; name=&quot;color&quot; value=&quot;#123456&quot; /&gt;&lt;/form&gt;
&lt;div id=&quot;colorpicker&quot;&gt;&lt;/div&gt;

1. Add a ready() handler to the document which initializes the color picker and link it to the text field with the following syntax:

&lt;script type=&quot;text/javascript&quot;&gt;
  $(document).ready(function() {
    $(&#39;#colorpicker&#39;).farbtastic(&#39;#color&#39;);
  });
&lt;/script&gt;

See demo1.html and demo2.html for an example (jquery.js is not included!).

**Styling**
--------------------------------------

The color picker is a block-level element and is 195x195 pixels large. You can control the position by styling your placeholder (e.g. floating it).

Note that the black/white gradients inside wheel.png and mask.png were generated programmatically and cannot be recreated easily in an image editing program.

**Advanced Usage**
--------------------------------------

**jQuery Method**

$(...).farbtastic()
$(...).farbtastic(callback)

This creates color pickers in the selected objects. callback is optional and can be a:

- _DOM Node_, _jQuery object_ r _jQuery selector_: the color picker will be linked to the selected element(s) by syncing the value (for form elements) and color (all elements).
- _Function_: this function will be called whenever the user chooses a different color.

**Object**

$.farbtastic(placeholder)
$.farbtastic(placeholder, callback)

Invoking $.farbtastic(placeholder) is the same as using $(placeholder).farbtastic() except that the Farbtastic object is returned instead of the jQuery object. This allows you to use the Farbtastic methods and properties below.

Note that there is only one Farbtastic object per placeholder. If you call $.farbtastic(placeholder) twice _with the same placeholder_, you will get the same object back each time.

The optional callback argument behaves exactly as for the jQuery method.

**Methods**

.linkTo(callback)

Allows you to set a new callback. Any existing callbacks are removed. See above for the meaning of callback.

.setColor(string)

Sets the picker color to the given color in hex representation.

.setColor([h, s, l])

Sets the picker color to the given color in normalized HSL (0..1 scale).

**Properties**

.linked

The elements (jQuery object) or callback function this picker is linked to.

.color

Current color in hex representation.

.hsl

Current color in normalized HSL.