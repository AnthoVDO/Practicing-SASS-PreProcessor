# Note about Sass

## Installing Sass

1) Go to Sass Github(https://github.com/sass/dart-sass/releases/tag/1.26.10)>select your device
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


