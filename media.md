# Media: Images

There has recently appeared a well-functioning **aspect-ratio** function in CSS, which can easily force the container to maintain the desired proportions. However, it is not supported in IE and older versions of popular browsers, so if you need to maintain old browsers, use the following trick.

##  Percentage Padding 
Percentage padding always takes the width of the parent, thus, `padding-top: 10%` will be equal to 10th of the parent's width. You only need to add the child elements into this container using absolute positioning.

Divide height by width and wrap in percentage.
Example: percenatege(9 / 16) = 56.25%

```
.parent {
    position: relative;

    &::before {
        content: '';
        display: block;
        padding-top: percenatege(9/16);
    }
    
.child-image,
.child-video {
    position: absolute;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
}
```