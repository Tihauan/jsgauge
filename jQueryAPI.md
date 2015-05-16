# Introduction #

This page describes the jQuery API provided by jsgauge. Note that in order to use this API you need to include both `gauge.js` and `jquery.gauge.js` - or their minified versions.

The plugin creates a new jQuery function called `gauge`.

The <a href='http://jsgauge.googlecode.com/svn/trunk/src/example/jquery-example.html'>Simple jQuery Example</a> page contains a small, complete example of how to use this plugin.

# Methods #

  * [init](jQueryAPI#init.md)
  * [setValue](jQueryAPI#setValue.md)
  * [draw](jQueryAPI#draw.md)



&lt;hr /&gt;



## init ##

Creates a new gauge control. The jQuery selector should point to a canvas tag:

```
jQuery("#test_overflow_max").gauge('init', options);
```

See [API#Options](API#Options.md) for more information on available options.

Note that a gauge may also be initialized by calling the `gauge` function without any arguments:

```
jQuery("#test_overflow_min").gauge();
```



&lt;hr /&gt;



## setValue ##

Changes the value displayed on the gauge:

```
jQuery("#test_overflow_max").gauge('setValue', 115); 
```



&lt;hr /&gt;



## draw ##

Redraws the gauge:

```
jQuery("#test_overflow_max").gauge('draw'); 
```



&lt;hr /&gt;



# Options #

See [API#Options](API#Options.md).