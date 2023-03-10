# Hover and Transitions

## Active state

Make sure to add styles for the active state to interactive elements, such as buttons and links. If the designer didn't provide the necessary details, use your sense of beauty to indicate the active state by for example changing the color of a button or scaling an icon. And of course, ping the designer, let them take a look at your perspective and suggest their own.

All in all, any clickable element must have an active state so that the user is aware that it can be interacted with. 
cursor property: pointer; is also required for all clickable elements.

## Transitions
Don't forget to add at least a simple transition for the active state. It will make things look much better than just an instant jerky switch.

```
.link {
    color: $color-black;
    transition: color 0.3s linear;
    
    @include hover-focus {
        color: $color-red;
    }
}
```


![#f03c15](https://placehold.co/15x15/f03c15/f03c15.png) BAD:
```
.element {
    transition: all 0.5s ease;
}
```
![#c5f015](https://placehold.co/15x15/c5f015/c5f015.png) GOOD:

```
.element {
    transition: bacground-color 0.3s linear, color 0.3s linear, 
}
```
 