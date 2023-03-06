# Responsive 

## Viewports

What viewports do we support?
We support all viewports from 320 wide (iPhone 5) to 4k screens.
But since no one makes designs for 4k, you just need to make sure that everything looks ok on them. 

### Mobile-first approach
Create a mobile version first, then pass over to the desktop.

```
.nav {
    &__list {
        display: flex;
        align-items: center;
        
        @include desktop {
            justify-content: space-between;
        }
    }
    
    &__item {
        padding: 12px;
        font-size: 16px;
        
        @include desktop {
            padding: 20px;
        }
    }
}
```

### Tablet designs
It's often the case that there are no separate designs for tablets. So use your sense of beauty to get a decent variation of the existing mobile and desktop designs.

### Breakpoints
We have a separate .scss file **breakpoints.scss** with a list of all possible breakpoints used on the project

```
$mobile-width: 320px;
$tablet-width: 768px;
$tablet-xl-width: 1024px;
$desktop-width: 1200px;
$desktop-xl-width: 1920px;

@mixin mobile {
  @media (min-width: #{$mobile-width}) {
    @content;
  }
}

@mixin tablet {
  @media (min-width: #{$tablet-width}) {
    @content;
  }
}

@mixin tablet-xl {
  @media (min-width: #{$tablet-xl-width}) {
    @content;
  }
}

@mixin desktop {
  @media (min-width: #{$desktop-width}) {
    @content;
  }
}

@mixin desktop-xl {
  @media (min-width: #{$desktop-xl-width}) {
    @content;
  }
}
```