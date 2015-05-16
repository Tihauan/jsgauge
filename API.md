# Introduction #

This page describes the API for the pure JavaScript `Gauge` component.


# Methods #

  * [Gauge](API#Gauge(_canvas,_options_).md)
  * [setOptions](API#setOptions_(_value_).md)
  * [setValue](API#setValue_(_value_).md)
  * [draw](API#draw_().md)



&lt;hr /&gt;



## Gauge( canvas, options ) ##

Gauge constructor, call this using `new` to create an instance of the gauge:

```
new Gauge( document.getElementById( 'test_default' ) );
```

To create a gauge, you need a reference to a `canvas` tag that you would like to use for the gauge, for example:

```
<canvas id="test_default" width="250" height="250"></canvas>
```

**Arguments**:

  * canvas - Reference to a DOM object containing the `<canvas>` tag to use for the gauge.
  * options - Object of optional parameters; see [options](API#Options.md) section below for details.



&lt;hr /&gt;



## setOptions ( value ) ##

Changes the initial gauge options on the fly. To update the display, call draw() or setValue() after setting the new options.

**Arguments**:

  * value - Options object, see below.



&lt;hr /&gt;



## setValue ( value ) ##

Changes the value displayed on a gauge.

**Arguments**:

  * value - Numeric value to display.



&lt;hr /&gt;



## draw () ##

Redraws the gauge.



&lt;hr /&gt;



# Options #

  * [value](API#value.md)
  * [valueFormat](API#valueFormat.md)
  * [label](API#label.md)
  * [unitsLabel](API#unitsLabel.md)
  * [min](API#min.md)
  * [max](API#max.md)
  * [majorTicks](API#majorTicks.md)
  * [minorTicks](API#minorTicks.md)
  * [bands](API#bands.md)
  * [colorOfText](API#colorOfText.md)
  * [colorOfWarningText](API#warningText.md)
  * [colorOfFill](API#colorOfFill.md)
  * [colorOfPointerFill](API#colorOfPointerFill.md)
  * [colorOfPointerStroke](API#colorOfPointerStroke.md)
  * [colorOfCenterCircleFill](API#colorOfCenterCircleFill.md)
  * [colorOfCenterCircleStroke](API#colorOfCenterCircleStroke.md)
  * ~~[greenFrom](API#greenFrom.md)~~
  * ~~[greenTo](API#greenTo.md)~~
  * ~~[yellowFrom](API#yellowFrom.md)~~
  * ~~[yellowTo](API#yellowTo.md)~~
  * ~~[redFrom](API#redFrom.md)~~
  * ~~[redTo](API#redTo.md)~~
  * ~~[redColor](API#redColor.md)~~
  * ~~[yellowColor](API#yellowColor.md)~~
  * ~~[greenColor](API#greenColor.md)~~




&lt;hr /&gt;



## value ##

Value to display on the gauge using both the text label at the bottom of the gauge and the needle.

**Type**: `Number`

**Default**: `0`



&lt;hr /&gt;



## valueFormat ##

A function that accepts two parameters (value, decimals) and returns a string value to be displayed for that specific value.

**Type**: `Function`



&lt;hr /&gt;



## label ##

Text label to display at the top of the gauge.

**Type**: `String`

**Default**: `''`



&lt;hr /&gt;



## unitsLabel ##

Text to display after the gauge value to indicate the type of units. For example, when displaying a temperature value you might include a degree symbol:

```
unitsLabel: '' + String.fromCharCode(186)
```

**Type**: `String`

**Default**: `''`



&lt;hr /&gt;



## min ##

Minimum value to display on the gauge; indicated by a small text label on the left-hand side of the gauge.

**Type**: `Number`

**Default**: `0`



&lt;hr /&gt;



## max ##

Maximum value to display on the gauge; indicated by a small text label on the right-hand side of the gauge.

**Type**: `Number`

**Default**: `100`



&lt;hr /&gt;



## majorTicks ##

Number of "large" ticks around the inner rim of the gauge.

**Type**: `Number`

**Default**: `5`



&lt;hr /&gt;



## minorTicks ##

Number of small ticks between each pair of major ticks.

**Type**: `Number`

**Default**: `2`



&lt;hr /&gt;



## bands ##

Array of objects used to define colored bands along the inner rim of the gauge. Each object contains the following members:

  * color - Color of the band
  * from - Value that the band starts at
  * to - Value that the band ends at

For example:

```
bands: [
   { color: '#ccc', from: 0, to: 10 },
   { color: '#ddd', from: 10, to: 20 }
]
```

**Type**: `Array`

**Default**: `[]`



&lt;hr /&gt;



## colorOfText ##

Color of text displayed on the gauge.

**Type**: `String`

**Default**: `'rgb(0, 0, 0)'`



&lt;hr /&gt;



## colorOfWarningText ##

Color to use for warning situations, for example when displaying a value outside the min/max range.

**Type**: `String`

**Default**: `'rgb(255, 0, 0)'`



&lt;hr /&gt;



## colorOfFill ##

Fill colors used to draw the gauge.

**Type**: `Array`

**Default**: `[ '#111', '#ccc', '#ddd', '#eee' ]`



&lt;hr /&gt;



## colorOfPointerFill ##

Color to use to fill the needle.

**Type**: `String`

**Default**: `'rgba(255, 100, 0, 0.7)'`



&lt;hr /&gt;



## colorOfPointerStroke ##

Color to use for the outline of the needle.

**Type**: `String`

**Default**: `'rgba(255, 100, 100, 0.9)'`



&lt;hr /&gt;



## colorOfCenterCircleFill ##

Fill color for the needle's center circle.

**Type**: `String`

**Default**: `'rgba(0, 100, 255, 1)'`



&lt;hr /&gt;



## colorOfCenterCircleStroke ##

Color to use for the outline of the needle's center circle.

**Type**: `String`

**Default**: `'rgba(0, 0, 255, 1)'`



&lt;hr /&gt;



## greenFrom ##

**Deprecated** Use the `bands` option to define the range of colored bands.

**Type**: `Number`

**Default**: `0`



&lt;hr /&gt;



## greenTo ##

**Deprecated** Use the `bands` option to define the range of colored bands.

**Type**: `Number`

**Default**: `0`



&lt;hr /&gt;



## yellowFrom ##

**Deprecated** Use the `bands` option to define the range of colored bands.

**Type**: `Number`

**Default**: `0`



&lt;hr /&gt;



## yellowTo ##

**Deprecated** Use the `bands` option to define the range of colored bands.

**Type**: `Number`

**Default**: `0`



&lt;hr /&gt;



## redFrom ##

**Deprecated** Use the `bands` option to define the range of colored bands.

**Type**: `Number`

**Default**: `0`



&lt;hr /&gt;



## redTo ##

**Deprecated** Use the `bands` option to define the range of colored bands.

**Type**: `Number`

**Default**: `0`



&lt;hr /&gt;



## redColor ##

**Deprecated** Use the `bands` option to define band colors.

**Type**: `String`

**Default**: `'rgba(255, 0, 0, 0.2)'`



&lt;hr /&gt;



## yellowColor ##

**Deprecated** Use the `bands` option to define band colors.

**Type**: `String`

**Default**: `'rgba(255, 215, 0, 0.2)'`



&lt;hr /&gt;



## greenColor ##

**Deprecated** Use the `bands` option to define band colors.

**Type**: `String`

**Default**: `'rgba(0, 255, 0, 0.2)'`