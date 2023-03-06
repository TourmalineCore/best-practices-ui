# Code style

## Naming 

## _CSS_
Use BEM methodology if there are no CSS modules or css-in-js on the project.

```
.block {
    $this: &;

    position: relative;
    width: 100vw;

    &__element-bg {
        position: absolute;
        top: 0;
        left: 0
        width: 100px;
        height: 100px;
        background-color: $color-green;
        
        &--right {
            left: auto;
            right: 0;
        }
        
        #{$this}--big & {
            width: 300px;
            height: 300px;
        }
    }
    
    &__element-border {
      border: 2px solid $color-black;
      
      #{$this}--large & {
          border-width: 6px;
      }
    }
}
```

Don't overload BEM elements.
If an element begins to contain two or more semantic attachments, it means that you most likely need to move such an element into a separate block.
Do not forget that each block must live in its own separate file.

![#f03c15](https://placehold.co/15x15/f03c15/f03c15.png) BAD:
```navigation.scss
.navigation {
    &__list {
        ...
    }
    
    &__item {
        ....
    }
    
    &__link {
        ...
    }
    
    &__item-list {
        ...
    }
    
    &__item-list-link {
        ...
    }
    
    &__item-list-icon {
        ...
    }
}
```

![#c5f015](https://placehold.co/15x15/c5f015/c5f015.png) GOOD:
```
navigation.scss
.navigation {
    &__list {
        ...
    }
    
    &__item {
        ....
    }
    
    &__link {
        ...
    }
}

navigation-list.scss
.navigation-list {
    ...
    
    &__link {
        ...
    }
    
    &__icon {
        ...
    }
}
```



## _CSS-selectors_
Don't use heavy selectors unless you really need to.
Don't use pure tags as part of a selector unless you really need to.
If you need to use a heavy selector to solve a problem, you might need to simplify something.

![#f03c15](https://placehold.co/15x15/f03c15/f03c15.png) BAD:
```
.block {
    $this: &;
    
    &__element {
        color: $color-white;
        
        .section .section--dark & {
            color: $color-black;
        }
    }
}
```

![#c5f015](https://placehold.co/15x15/c5f015/c5f015.png) GOOD:
```
.block {
    $this: &;
    
    &__element {
        color: $color-white;
    }
    
    #{$this}--dark & {
        color: $color-black;
    }
}
```

## _JS_

Use camel case for JS variables
```
const myAwesomeVariable = {};
```

Use meaningful names:
- variable's name must indicate what it contains
- method's name should indicate what it does
- if a variable contains an array/collection, add an -s postfix
