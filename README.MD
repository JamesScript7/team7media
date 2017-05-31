# Hello team members of team7media!
I've created this git repo to showcase some of my HTML5/CSS3 skills and also wrote up an overview of SASS to help me refresh my memory.

The transition from CSS to SASS is fairly simple as it carries out to solve repetition and flexibility through a programatic approach. It's a little bit of ruby, python and javascript!

# Getting set up with SASS:
1. install sass on the command line

'''
  sudo gem install sass
'''

2. Check the version to confirm. Should return: (Sass 3.4.22 (Selective Steve))

'''
  sass -v
'''

3. Enter the styles directory and run:

'''
sass main.sass output.css
'''

# The Important Stuff:

SASS drops the curly brackets and semi-colons! It also uses two-space indentations for code nesting.

## Variables

Re-using code is very efficient and bring CSS closer to programatic thinking.

* The "$" symbol creates a variable
* Insert the variable as a value for the property

## Nesting

This follows the DRY principles. Less typing = less time.

The CSS way:

'''
nav ul {
  padding: 5px;
}

nav li {
  display: inline-block;
}
'''

The SASS way:

'''
nav
  ul
    padding: 5px

  li
    display: inline-block
'''

Also any properties that have hyphenates prefixes can be nested as so:

'''
.header
  .menu
    .items
      font:
        weight: bold
        size: $variable + 2px
      background:
        position: fixed
        color: \#151515
'''

## Partials

These are chopped up pieces of a CSS file, mainly for re-usability. This modularizes the file so it can be used on different files. Place an underscore preceding the file name of the partial like so to let the file know it shouldn't be generated into the CSS file:

'''
  \_partial_blue_design.sass
'''

## Import

This is how we bring the partials into the current CSS file. When we import we can build on top of the current CSS file.
We have to remember that when we use \@import, it creates another HTTP request. SASS knows to drop the leading underscore and file

'''
\@import partial_blue_design
'''

## Mixins
## Extend/Inheritance
## Operators
##
