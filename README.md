# Modular Scale for Stylus
Modular scale calculator built into your Stylus http://modularscale.com

A modular scale is a list of values that share the same relationship. These values are often used to size type and create a sense of harmony in a design. Proportions within modular scales are all around us from the spacing of the joints on our fingers to branches on trees. These natural proportions have been used since the time of the ancient Greeks in architecture and design and can be a tremendously helpful tool to leverage for web designers.

Ems work especially well with modular scales as their recursive properties mimic modular scales making them more predictable and easier to manage. Pixels and other units work just fine and breakpoints in responsive web design can naturally fall on your scale to create better relevance to your text as all the values in your layout harmonize with each other.

To get started, you need to select a ratio and a base value. The base value is usually your text font size or 1em. Optionally you can add another value to create a double standard modular scale which might be useful to create more options for in-between values. This base size paired with a ratio such as the golden ratio or any musical proportion will create your scale of values which all share this proportion.

## Usage

Modular Scale has two default variables that you should place with your other site wide variables. `$ms-base` is usually your font size or `1em` and can have multiple values. `$ms-ratio` is the factor of change between each number so if the ratio is `1.5` then each number in the sequence will be 1.5 times that of the previous number. Just as you can have multiple bases you can have multiple ratios.

```stylus
$ms-base = 1em;
$ms-ratio = $golden;
```

Modular-scale is used as a function. Simply pass it through in place of any value to generate a value based on a modular scale.

```stylus
font-size: ms(2); // two up the modular scale
font-size: ms(2, 16px); // two up the modular scale with a base size of 16px, default is 1em
font-size: ms(2, 1em, $octave); // Same as above but on an octave scale
```

You can output a list to your terminal to help you find out what values are on your scale.

```stylus
p(ms-list($start, $end, $ms-base, $ms-ratio))
```

You can use a double standard scale by simply adding more base sizes in a space-separated list.  
**note:** the starting point of the scale will always be the **first** value in this list

```stylus
.double-standard {
  width: ms(7, 1em 2em);
}
```

You can do the same thing with ratios

```stylus
.multi-ratio {
  width: ms(7, 1em, $golden $octave);
}
```

You can use multiple $ms-bases and multiple $ms-ratio together

```stylus
.multibase-multiratio {
  width: ms(7, 16px 24px, $golden $fourth);
}
```

## Responsive scales

Based on [Mike Riethmuller’s](https://twitter.com/MikeRiethmuller) [_Precise control over responsive typography_](http://madebymike.com.au/writing/precise-control-responsive-typography/). A fantastic technique for fluidly scaling typography.

[See a responsive modular scale in action](http://lab.scottkellum.com/ms-respond.html).

First, you will need to set your range. A range is a list of ratio and breakpoint values from smallest to largest. Because this will render as a fluid range by default you will probably only want or need a range of two.

```stylus
$ms-range = 1.1   20em, 1.333 60em;
```

If you want to have specified steps instead of fluid type set `$ms-fluid` to `false` and you may want to add more values to your range.

```stylus
$ms-fluid = false;
$ms-range = 1.2 20em, 1.3 30em, 1.4 40em, 1.5 50em, 1.6 60em;
```

Now you can use the `ms-respond` mixin to output a range of values for a single point on a scale. The first value is the property and the second value is the point on the scale you wish to use. That’s it, a series of responisve values will be generated based on your configuration.

```stylus
foo {
    ms-respond(font-size, 2);
}
```

## Ratios

Modular scale includes functions for a number of classic design and musical scale ratios. You can add your own ratios as well.

By default, the variable `$ms-ratio` is set to `$golden`.

<table>

  <tr><th>Function</th><th>Ratio</th><th>Decimal value</th></tr>

  <tr><td>$phi</td><td>1:1.618</td><td>1.618</td></tr>
  <tr><td>$golden</td><td>1:1.618</td><td>1.618</td></tr>
  <tr><td>$double-octave</td><td>1:4</td><td>4</td></tr>
  <tr><td>$major-twelfth</td><td>1:3</td><td>3</td></tr>
  <tr><td>$major-eleventh</td><td>3:8</td><td>2.667</td></tr>
  <tr><td>$major-tenth</td><td>2:5</td><td>2.5</td></tr>
  <tr><td>$octave</td><td>1:2</td><td>2</td></tr>
  <tr><td>$major-seventh</td><td>8:15</td><td>1.875</td></tr>
  <tr><td>$minor-seventh</td><td>9:16</td><td>1.778</td></tr>
  <tr><td>$major-sixth</td><td>3:5</td><td>1.667</td></tr>
  <tr><td>$minor-sixth</td><td>5:8</td><td>1.6</td></tr>
  <tr><td>$fifth</td><td>2:3</td><td>1.5</td></tr>
  <tr><td>$augmented-fourth</td><td>1:√2</td><td>1.414</td></tr>
  <tr><td>$fourth</td><td>3:4</td><td>1.333</td></tr>
  <tr><td>$major-third</td><td>4:5</td><td>1.25</td></tr>
  <tr><td>$minor-third</td><td>5:6</td><td>1.2</td></tr>
  <tr><td>$major-second</td><td>8:9</td><td>1.125</td></tr>
  <tr><td>$minor-second</td><td>15:16</td><td>1.067</td></tr>

</table>

Add your own ratio in Stylus by setting a variable and passing that to modular-scale.

```stylus
$my-ratio = 1 / 3.14159265;
$ms-ratio = $my-ratio;
```

## Original SASS plugin

The [original version](https://github.com/modularscale/modularscale-sass) of this plugin was written in [SASS](http://sass-lang.com). If you have any comments or suggestions of impovements you can use [issue tracker of modularscale-sass repo](https://github.com/modularscale/modularscale-sass/issues).

## License

The MIT License (MIT)

Copyright © 2015 [Scott Kellum](http://www.scottkellum.com/) ([@scottkellum](http://twitter.com/scottkellum)), [Adam Stacoviak](http://adamstacoviak.com/) ([@adamstac](http://twitter.com/adamstac)) and [Mason Wendell](http://thecodingdesigner.com/) ([@codingdesigner](http://twitter.com/codingdesigner))

Version in [Stylus](https://github.com/stylus/stylus) syntax was implemented by [Denis Solovets](https://github.com/solovets)

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the “Software”), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

**The software is provided “as is”, without warranty of any kind, express or implied, including but not limited to the warranties of merchantability, fitness for a particular purpose and non-infringement. In no event shall the authors or copyright holders be liable for any claim, damages or other liability, whether in an action of contract, tort or otherwise, arising from, out of or in connection with the software or the use or other dealings in the software.**

