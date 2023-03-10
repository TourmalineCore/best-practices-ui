# Magic

Your code should not contain magic numbers, i.e. figures plucked from the air.
If you have some number or text that you need to calculate / compose, etc., don't write their value directly, better create a constant with a meaningful name for them in uppercase.

![#f03c15](https://placehold.co/15x15/f03c15/f03c15.png) BAD:
```
const getMatchEndDate = (matchStartDate) => {
    return +new Date(matchStartDate) + 5400;
}
```
 
![#c5f015](https://placehold.co/15x15/c5f015/c5f015.png) GOOD:
```
const STANDART_MATCH_DURATION = 5400;

const getMatchEndDate = (matchStartDate) => {
    return +new Date(matchStartDate) + STANDART_MATCH_DURATION;
}
```
## CSS Magic

All values that are reused in different parts of the project, especially systematically, should be stored  in variables.scss.

##  Magic of CSS sizes, paddings, margins, transforms, etc.
Of course, if we fret over semantics, we write almost the entire CSS using magic numbers, simply because the  designs suggest that way. So here we should act rationally.

Sometimes designers can reuse elements in their design programs without paying close attention to their dimensions or spacings. Sometimes the difference in sizes can be 2-3 pixels, sometimes 4-6 or even more. 
Proceed according to the principle of the average number, a multiple of 2 or 5. I.e. if the size is less than 30, caluclate the average and take a multiple of 2, if the spacing is greater than 30, caluclate the average, and take a multiple of 5.

If you are provided with a design system, use the dimensions and spacings specified there, even if you come across a padding that's out of line.

Sometimes it's worth adding a local scss variable, for example if you need to make a tricky absolutely positioned element, and take into account its size when inserting conten. Use the variable to calculate the offset indent (or the like). 

```
.promo-banner {
    $collage-image-width-desktop: 218px;
    
    position: relative;
    ...
    
    &__collage-image {
        position: absolute;
        z-index: 1;
        width: $collage-image-width-desktop;

        &--1 {
            top: 60px;
            left: 13%;
            width: 132px;

            @include desktop {
                left: calc(50% - #{$collage-image-width-desktop / 2});
                width: 218px;
            }
        }
    }
}
```

# Magical z-index

You have to be very careful when using z-index.

Remember that this property will not work for elements with `position: static`, i.e. for all elements by default.

If you need to put an element on top of the entire application, create a scss variable for it and put it in the variables.scss file. No need to set extremely large values, use values no more than a thousand in increments of tens or hundreds. 

```
$layer-alert-bar-container: 80;
$layer-prompt: 90;
$layer-header: 100;
$layer-element-spinner: 100;
$layer-cookie-bar: 200;
$layer-overlay: 300;
$layer-menu: 500;
$layer-modal: 700;
$layer-page-spinner: 1000;
```


To use z-index locally, set the value of the parent (block) to zero and you safely redefine the values of the elements. However, stay within the values from -10 to 10. 
```
.block {
    position: relative;
    z-index: 0;
    
    &__bg {
        position: absolute;
        z-index: -1;
    }
    
    &__play {
        position: absolute;
        z-index: 1;
    }
}
```

If you cannot do without magic numbers, add a comment (in English) describing why you did it that way.
 