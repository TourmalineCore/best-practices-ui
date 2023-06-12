# Layout

## Box-sizing
to simplify the calculation of elements dimensions 
```
*,
*::before,
*::after {
    box-sizing: border-box;
}
```

## Modal and PageScroll
```
.html {
    position: relative;
    overflow-x: hidden;
    overflow-y: scroll;
    height: 100%;
    font-size: 100%;
    -webkit-overflow-scrolling: touch;

    &.is-blocked {
        overflow: hidden;
        
        .compensate-scroll {
            padding-right: var(--scrollbar);
        }
    }

    &.is-blocked-touch {
        position: fixed;
        overflow-y: scroll;
        width: 100%;
        height: auto;
    }
}
```

## Container
To horizontally center the content
```
.container {
    max-width: $container-max-width;
    margin-right: auto;
    margin-left: auto;
    
    &--small {
        max-width: $container-max-width-small;
    }
    
    &--middle {
        max-width: $container-max-width-middle;
    }    
}
```

## Margins and paddings
You should differentiate between the logic of margins and the logic of paddings. 
For example, we have a list of cards in a row - it's worth wrapping each card into the element called  **"block__item"** that will get the outer spacings (margins), whereas the card itself will get the inner spacings (paddings).
 
```
.block {
    &__list {
        display: flex;
    }
  
    &__item {    
        & + & {
            margin-left: 10px;
        }
    } 
  
    &__card {
        padding: 10px;
        background-color: $color-blue;
    }
  
    &__link {
        font-size: 12px;
        color: $color-yellow;        
    }
}
```

## Component spacings

In case you are using **components approach** on the project (and **expecially, if the components are managed in CMS**), make sure you take an effort to discuss the logic of vertical spacings between components togerther with the designer and come up with consistent rules that you will follow during the development. 
Otherwise, you are guaranteed to get bugs that the spacings do not match the design because content managers are free to come up with any combination of components order.

Possible style rules may look like this:

```
.components {
    $this: &;

    &__item {
        #{$this} > & ~ & {
            margin-top: $default-mobile-vertical-gap-between-components;

            @include tablet {
                margin-top: $default-desktop-vertical-gap-between-components;
            }

            &:last-child {
                margin-bottom: $default-mobile-vertical-gap-between-components;

                @include tablet {
                    margin-top: $default-desktop-vertical-gap-between-components;
                }

                .components & {
                    margin-bottom: 0;
                }
            }

            &--big:last-child {
                margin-bottom: 0;
            }
        }
    }
}
```
