##### Personnal note
 - How to make an arrow check: Le préprocesseur SASS(6/11): Les mixins at 07:00# 

 - Better to use REM for the font-size

Note about Sass

## Installing Sass

1) Go to Sass Github( https://github.com/sass/dart-sass/releases/tag/1.26.10 ) >select your device
2) Move the downloaded folder to your project path>unzip
3) Open Your IDE
4) Open the terminal
5) creat Sass folder
6) creat style.scss inside the created folder
NOTE: I installed the file here but it's possible to install it on the computer and have access for all the projects. I just did it for this repo

## Checking the command with help

check the dart-sass path and write it inside the terminal with --help to see the line.
For exemple, my command will look like this: ./dart-sass/dart-sass/sass --help

## Creat a style.css and a style.css.map file 

you need to add the following line to the terminal: sass/style.scss style.css
of course, don't forget to used the good path for exemple, I have: 
./dart-sass/dart-sass/sass sass/style.scss style.css

This command creat a style.css file and a style.css.map.

## Ignore file

Don't forget to creat a git ignore file to ascape style.css.map file on github for exemple.
Here, I keep it for the note purpose

## Automatic update

To Avoid to spend you time to used the terminal to see the change inside the style.css file, you can add the flag --watch
For exemple:
./dart-sass/dart-sass/sass sass/style.scss style.css --watch
If it's correctly done, you will see this message inside the terminal while saving your change : Compiled sass\style.scss to style.css.
It also show you your mistake !

## Map use

Map file is used to see the element inside the original SCSS file in a browser and not the compiled file.
It's easier to change the code in the futur because we can directly find the line inside the SCSS file because, normaly, this is the style.css which is related to the index.html file.

## Import file 

SaSS is used to import easily file to avoid having too much line code.
For exemple, you would like to use the minireset lib but you want to avoid too much extra line code.
1) creat a sub folder named libs
2) go to https://jgthms.com/minireset.css/  and click on download.
3) copy the Css code 
4) past the Css code inside a new file that you creat inside the subfolder named libs. Let say reset.scss
5) go to style.scss and import before body the libs: @import "libs/reset.scss";

Now, you only have on line code

## Nesting element 

With SaSS, we can nest element inside each other.
For exemple instead of making a line with 
h1 {
    color:red;
    } 
and then 
h1 a {color: green;}
, we can do 
h1{
    color:red; 
a{
    color:green;
    }
}

if we want to use a selector just after like :hover, we need to use a & to notifie it.
Exemple: 
.btn {
    background-color: blue;
    &:hover{
        background-color: red;
    }
}

we can also nest to have multiple component condition

exemple:

.btn {
    background-color: blue;

    .green-theme & {
        background-color: darkblue; /*Here, it's like we did .green-theme .btn {background-color: darkblue;}*/
    }
}

It's also possible to use the media query inside but it's better to use an other preprocessor for the media query

For more info, don't forget that there is a documentation on the website



## Extend

Sometimes, we have some css for some class that we would like to reuse for other elements.
To do so, we can use the extend methode.
exemple:

.btn {
    color:red;
}

call-to-action {
    @extend .btn;
}

it will give something like this:

.btn, call-to-action {
    color:red;
}

This methode is usefull while we are using the padding, margin, ...

## False selector

This is a selector starting with % and which won't be inside the CSS style sheet.
It's used to make general parameter.
Exemple: %btn {}
then we can use the extend method to add to the SCSS.
exemple:
.btn{
    @extend %btn; /* .btn will get %btn parameter*/
}
This methode is used to make cleaner code. Of course, we can use the normal methode where we set the .btn and then .btn-danger.

NOTE: Do not abuse with this selector because it add weight to the file

## Variable

Less use now because CSS have also variable but still interesting to use

### Creat a Variable

To creat a Variable, we just need to use the $ sign, then the name of the variable and then the value.
Exemple:

$primary: blue;

Here, I used only one value, but you can add more value like pixel number, ...

### Use a Variable
To use a Variable, we just need to insert it.
Exemple:
color: $primary;

### Pro about SASS variable

We can make calculus operation
The css generated by SASS has better navigator compatibility

### Using variable inside selector

If we want to use variable inside selector like media query, we need to surround it by #{}.
Exemple:
@media #{medium-up}{
    .btn {
        width: 100%;
    }
}

### Warning about Variable use

If a variable is set at multiple place, this is the last who win !
But we can add after the value !default to use this value if the variable isn't defined after.
exemple: $medium: 768px!default;
Here, the system will apply 768px ONLY if the variable named medium isn't defined.

## Function

### Darken
get a color darker

darken(color, % I want it darker)
exemple: darken(blue, 10);
I will get the color blue 10% darker

### Lighten
get a color lighter
lighten(color, %)
exemple: lighten(blue, 10);
I will get the color blue 10% lighter

Darken and Lighten don't use black but it use contrast.

For more function, don't forget to go to the firstclass function on the SASS website. https://sass-lang.com/documentation/modules

## Mixins

Mixins are used to avoid repeating code block
For exemple, adding -ms-transform and -webkit-transform, ...

when we used mixin, we need to use @include instead of @extend.
The difference between the 2 are that @extend will creat each time an entire new line condition for each.
The @include will group all inside a condition
Mixin can have default value and a argument to change the value quickly.
Exemple:
@mixin rotate($rotation: 10deg){
    -ms-transform: rotate($rotation);
    transform: rotate($rotation);
    -webkit-transform: rotate($rotation);
}

.card {
    rotate(60deg);
}

Here, the rotate mixin will give a 10deg rotation if we don't precise the 60deg rotation.



## Own function

to creat our own function, it's a little like javascript with different synthaxe.

@function name(argument){
    @return argument*2
}

Went we creat function and playing with different kind of value like em, px and rem, we can have some difficulties to convert value.
In that case, we can go on CSS-Tricks>snippets>sass>strip unit function.
https://css-tricks.com/snippets/sass/strip-unit-function/


