#Installation:

http://rubyinstaller.org/downloads/

set PATH=%PATH%;C:\Ruby22\bin

https://github.com/kingjulien/workshop-sass

cd to your folder....

gem install sass

sass -v

sass --watch sass:public/css

open file sass/columns.scss & save it

check if you have file columns.css created under public/css

check your index.html in browser

**Installed!**

##Tasks:

###1. Nesting
- check how nesting is done in scss and what is the result in css
- rewrite sources/nav.css to sass/nav.scss
  (if it's correct, compiled nav.css should be same as in resources)
- rule of 3 nesting - remove 4th nesting by changing nav ul li to ul > li

###2. Importing
    @import "columns"; // notice it's just name of file (without .scss)
    @import "nav";

- import nav.css and columns.css into 1 file - main.css - so you can have just 1 link to css in html - main.css

###3. Reference parent
    a {
        &:hover {
        }
    }

- change background color to #222; of last li a

###4. Variables
**$text-color**: #333;
- create & use variables for all colors & sizes
   
###5. Operations
In SASS you can **calculate colors**
- try to calculate 1 new colour by using 2 already defined colors: 
- color-1 + color-2
- color-1 - color-2

- define variables for grid: **grid-width** & **grid-columns**
- calculate width in % for element which width should be 3 of 12 columns and use it for some selector, f.e. .col3 - width should be in % (25%)

    width: (($grid-width / $grid-columns) * 3 / $grid-width) * 100%;

###6. Mixins
    A mixin lets you make groups of CSS declarations that you want to reuse throughout your site. You can even pass in values to make your mixin more flexible. A good use of a mixin is for vendor prefixes, f.e. border-radiu.
    
    syntax:
      @mixin rounded-corners($radius) {

      }

      @include rounded-corners(10px);
    
- create and use mixin for border-radius with those lines:

      -webkit-border-radius: ...;
      -moz-border-radius: ...;
      -ms-border-radius: ...;
      -o-border-radius: ...;
      border-radius: ...;
- create and use mixin on h1 with those css rules:

        background-color: $color;
        border-color: darken($color, 30%);
        color: darken($color, 40%); // notice - you can use functions inside mixins
        .syntax { // notice - you can use nesting inside mixins
          color: darken($color, 30%);
        }

###7. Extending / Inheritance
- extend .errorMesssage from .error
    
    @extend .error;

###8. functions
    prebuilt, f.e. color - darken($color, $amount)

- create and use custom function for calculating width of column in % based on number of columns
    
###9. Media queries nesting
- define breakpoints as variables and nest some media queries

    @media screen and (max-width: $break-small) {
    
    }

###10. Final - media queries mixins using @content
    just use mixin 'breakpoint'

    @mixin breakpoint($name){
      @if $name == small-screen {
        @media only screen and (min-width: $small-breakpoint) {
          @content
        }
      }
      @if $name == medium-screen {
        @media only screen and (min-width: $medium-breakpoint) {
          @content
        }
      }
      @if $name == large-screen {
        @media only screen and (min-width: $large-breakpoint) {
          @content
        }
      }
    }


Bonus:
compass
sprites - http://compass-style.org/help/tutorials/spriting/
