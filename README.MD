# Intro to Sass!
A simple overview of Sass.

The transition to Sass from CSS is relatively simple. It carries out to solve repetition and add flexibility.

I will be writing in Sass syntax instead of SCSS. The difference is minor and easy to convert.

## Getting set up with Sass:
1. install Sass on the command line.

```
sudo gem install Sass
```

2. Check the version to confirm.

```
Sass -v
```

As of June 05, 2017, should return:

```
Sass 3.4.22 (Selective Steve)
```

3. Enter the styles directory and run:

```
Sass main.sass output.css
```

4. Watch it so that Sass will update every time the Sass file detects a change:


watch a single file:
```
Sass --watch input.sass:output.css
```

watch a directory:
```
Sass --watch app/sass:public/stylesheets
```

## The Important Stuff:

1. Sass drops the curly brackets and semi-colons!
2. It also uses two-space indentations for code nesting.
3. SCSS and Sass are easily convertible to CSS.

### Variables

Re-using code is very efficient and bring CSS closer to programmatic thinking.

* The "$" symbol creates a variable
* Insert the variable as a value for the property
* Using functions and loops!

### Nesting

This follows the DRY principles. Less typing = less time = more ads = more money in your pocket!

The CSS way:

```
nav ul {
  padding: 5px;
}

nav li {
  display: inline-block;
}
```

The Sass way:

```
nav
  ul
    padding: 5px

  li
    display: inline-block
```

Also any properties that have hyphenates prefixes can be nested as so:

```
.header
  .menu
    .items
      font:
        weight: bold
        size: $variable + 2px
      background:
        position: fixed
        color: #151515
```

### Partials

These are chopped up pieces of a CSS file, mainly for re-usability. This modularizes the file so it can be used on different files. Place an underscore preceding the file name of the partial like so to let the file know it shouldn't be generated into the CSS file:

```
_partial_blue_design.Sass
```

### Import

This is how we bring the partials into the current CSS file. When we import we can build on top of the current CSS file.
We have to remember that when we use \@import, it creates another HTTP request. Sass knows to drop the leading underscore and file extension.

```
@import partial_blue_design
```

### Mixins

This is where things get fun with function capabilities!
You have the ability to pass in an argument between the parenthesis. The benefit here is that you enter the value once and it get applied to multiple properties! It really helps with browser compatibility code.

* You can set the default argument. For example:

```
=border-radius($radius: 3px)
  -webkit-border-radius: $radius
  -moz-border-radius:    $radius
  -ms-border-radius:     $radius
```
*note: SCSS syntax uses "\@mixin" where as Sass uses "="*

### Include

this brings in the mixin you created

```
.box
  +border-radius(5px)
```
*note: SCSS syntax uses "\@include" where as the Sass uses "+"*

So if you give an argument, it will use that. If you leave off the (5px) then it will use the default value specified in the creation of the mixin.

### Extend/Inheritance

This allows you to bring over the set of CSS properties.

```
.test
  width: 80%
  margin: 0 auto

.new
  @extend .test
  border-color: yellow
```

### Operators

Basically you can use math operators to create dynamic sizing based on a set window size. Lets say for any reason, you need to convert pixel value to a percentage:

```
.content-one
  width: 400 / 1000 * 100%

.content-two
  width: 600 / 1000 * 100%
```

### Loops

This is an each-loop that is similar to a for in loop

```
$list: (orange, purple, teal)

@each $item in $list
  .#($item)
  background: $item
```

This is a for-loop

*note: You can use "through" or "to" keywords*

```
$total: 10
$step: 360deg / $total

@for $i from $begin through $end
  .wheel:nth-child(#{$i})
  background: adjust-hue(blue, $i * $step)
```
