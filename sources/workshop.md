Installation:

http://rubyinstaller.org/downloads/

prompt: set PATH=%PATH%;C:\Ruby22\bin

cd to your folder....

gem install sass
check: sass -v

create folders:
sass
public/css

cmd: sass --watch sass:public/css


create file main.scss
check if you have file created under public/css
check your index.html in browser

Installed!

check how nesting is done in scss and what is the result in css


Tasks
Basics:
0. importing
    import nav.css and columns.css into 1 file - main.css - so you can have just 1 link to css in html

1. nesting
Prepisat sources/nav.css do sass/nav.scss
Ak je to spravne, mal by byt css/nav.css rovnaky ako sources/nav.css

2. rule of 3 nesting - remove 4th nesting - nav ul li -> nav li

3. reference parent

4. apply rules to first level li only
    - > ul > li /* first level */,
5. apply last-child - change background color of last li a
    &:last-child{
      a {
        background-color: #222;
      }
    }

6. variables
    create & use variables for colors & sizes

    $text-color: #333;

7. operations
    spocitat/odcitat 2 farby: color-1 + color-2

8. zadefinujte si variables grid-width a pocet stlpcov v gride a priradte nejakemu selectoru, napr. col-3 width v %, ak element ma byt na 3 stlpce gridu
    width: (($grid-width / $grid-columns) * 3 / $grid-width) * 100%;


9. mixins
    sluzia na opakovane casti kodov, cize macro, napr. rozne prefixy pre rozne browsere ale kludne aj casti css
    vytvorte a pouzite mixin na toto:

      -webkit-border-radius: ...;
      -moz-border-radius: ...;
      -ms-border-radius: ...;
      -o-border-radius: ...;
      border-radius: ...;

      a druhy na tuto cast kodu:
      background-color: $color;
      border-color: darken($color, 30%);
      color: darken($color, 40%);
      .close {
        color: darken($color, 30%);
      }

      syntax:
      @mixin rounded-corners($radius) {

      }

      @include rounded-corners(10px);

10. extending / inheritance
    extend .errorMesssage from .error

11. functions
    prebuilt, f.e. color - darken($color, $amount)

    create custom function for calculating width of column in % based on number of columns

12. media queries nesting
    define breakpoints as variables and nest some media queries

13. final - media queries mixins using @content
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
