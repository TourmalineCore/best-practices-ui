# Accessibility

Accessibility is not just about visually impaired people. Primarily, it is about the ability to navigate a website using the keyboard, because the keyboard is something that both completely healthy people and people with disabilities use on a daily basis. And secondarily, accessibility is about people with disabilities.
You can find yourself in the situation when your mouse is broken, but you need to be able to navigate the website here and now. And if the website does not allow you to do it using the keyboard, this is a real problem. However, developing a website for screen readers is trickier than for ordinary visual perception.
As a rule, it doesn’t matter to us what tags are used and what is nested inside them, but it is crucial for screen readers.
Take a form that you need to fill out as an example - you need to be able to switch between inputs using the tab key and clearly see which input is in focus.


## Semantic tags

Semantic tags were designed specifically for visual highlighting and so that screen readers could navigate between them. And if you use semantic tags, you can even style the page a bit without using css, because the browser has built-in styles for them. 
In our work, however, native styles hinder more than help - we have to use resets and normalizers.
Any way, you should always opt out for using semantic tags, as they really increase readability.

![#f03c15](https://placehold.co/15x15/f03c15/f03c15.png) BAD:
```<div class="section">
    <div class="block">
        <div class="block__inner">
            <div class="block__list">
                <div class="block__item">
                    <span>item 1</span>
                </div>
                <div class="block__item">
                    <span>item 2</span>
                </div>
            </div>
        </div>
    </div>
    <div class="block">
        <div class="block__inner">
            <div class="block__list">
                <div class="block__item">
                    <span>item 3</span>
                </div>
                <div class="block__item">
                    <span>item 4</span>
                </div>                
            </div>
        </div>
    </div>
</div>
```

![#c5f015](https://placehold.co/15x15/c5f015/c5f015.png) GOOD:
```
<section class="section">
    <article class="block">
        <div class="block__inner">
            <ul class="block__list">
                <li class="block__item">
                    <h2>item 1</h2>
                </li>
                <li class="block__item">
                    <h2>item 2</h2>
                </li>
            </ul>
        </div>
    </article>
    <article class="block">
        <div class="block__inner">
            <ul class="block__list">
                <li class="block__item">
                    <h2>item 3</h2>
                </li>
                <li class="block__item">
                    <h2>item 4</h2>
                </li>                
            </ul>
        </div>
    </article>
</section>
```

## ALT
ALT is a REQUIRED attribute when using images, its value must reflect what is shown in the image. This is a very important criterion, because if we ignore it, we will not meet even accessibility level A.

## Button or link?
If an element leads us somewhere, i.e. to another page, it is a link. Otherwise, it is a button.
Don't forget to add the type=”button” attribute to each button, otherwise the browser will consider this button as a submit for the form, which is not semantical, and if the button gets inside the form, the form will be submitted on each click.
### Button within a button
It is a no-go to place one active element within another active element, be it a button within a link, a link within a button, a link within a link, etc.

## Lists
If you see duplicated items, make a list. 
E.g. three or more links/buttons/cards in a row, a grid of cards, elements in navigation, etc.

## Titles
We must follow the order of headings on the page, i.e. you cannot place h1 between h2 and h2, which are on the same level, or the page cannot first have h2 and then h1.
Every page must have one h1.
If you are not sure which heading to choose, the size of the component can help you with that. E.g. use h2 for a section, h3 for a card.


## Links
The link must not lead to itself, i.e. the link should not lead to the page where it is placed, this is bad for semantics, for SEO, for accessibility.
For example, a company logo in the navigation. As a rule, it is made as a link to the home page. But on the homepage itself, this link logo should turn into h1.

## visually-hidden
This allows you to visually hide an element, but it will remain available to readers and indexer bots.

```
.visually-hidden {
    position: absolute;
    overflow: hidden;
    clip: rect(0 0 0 0);
    clip-path: inset(100%);
    width: 1px;
    height: 1px;
    margin: -1px;
    padding: 0;
    border: 0;
    white-space: nowrap;
}
```

## Downloading status
If your component calls the api and waits for a response, show the user that the download is in progress. Use the spinner/skeleton.
Along with showing the spinner, block necessary buttons so that clicking on them would not break the component.

### Handling errors on asynchronous requests
Keep in mind that a request can fail, for example because of the user's network connection. 

## Tools
**Axe** is a browser plugin that diagnoses what needs to be fixed on your page.
**Voice over** for iPhone and iMac