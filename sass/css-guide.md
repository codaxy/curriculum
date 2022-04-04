# CSS and SCSS Guide

## Inserting CSS [A]
There are 3 ways of inserting CSS.
#### [Inline] [A]
``` html
    <h1 style='color: red; font-size: 20px;'>Heading</h1>
```
#### [Internal] [A]
```html
    <head>
        <style>
            p {
                color: red;
                font-size: 20px;
            }
        </style>
    </head>
```
#### [External] [A] (recommended)
```html
    <head>
        <link rel="stylesheet" type="text/css" href="/styles/myStyle.css">
    </head>
```

#### [External using @import]
```html
    <head>
        <style>
            @import url("/styles/myStyle.css");
        </style>
    </head>
```

## Syntax [A]
A CSS rule-set consists of a selector and a declaration block.
<img src='./images/csssyntax.png' />

## Selectors
A CSS selector is the part of a CSS rule set that shows which element (class, id,...) will be styled by the applied `property:value` declarations.

Selectors can be divided in these categories:
#### [Simple selectors] [A]
Match one or more elements based on element ``type``, ``class``, or ``id``.
```CSS
    p { color: red };
    .red-text { color: red };
    #red { color: red };
```

#### [[Pseudo-classes] [A]](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes)
Match states of elements, such as `:hover`, `:focus`, or their position in DOM tree: `:first-child`, `:last-child`...
```CSS
    p:hover { color: lightred };
    p:first-child { color: lightred };
```

#### [[Attribute selectors] [B]](https://developer.mozilla.org/en-US/docs/Web/CSS/Attribute_selectors)
Match one or more elements based on their attributes/attribute values. 
```CSS
    a[href="https://example.org"] {
        color: red;
    }
```
#### [[Pseudo-elements] [D]](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-elements)
Examples: `:after`, `:before`, `:first-line`...
```CSS
    p:after {
        content: '';
        position: absolute;
        left: 0;
        bottom: 0;
        height: 100%;
        background-color: red;
        width: 2px;
    }
```

#### [[Universal selectors] [B]](https://developer.mozilla.org/en-US/docs/Web/CSS/Universal_selectors) 
Selector `*` will match all elements.
```CSS
    .header * {
        color: red; /* every element inside header will have red color */
    }
```

#### [[Combinators] [C]](https://developer.mozilla.org/en-US/docs/Learn/CSS/Introduction_to_CSS/Combinators_and_multiple_selectors)
- **Adjacent sibling selectors** `.a + .b`
- **General sibling selectors** `.a ~ .b`
- **Child selectors** `.a > .b`
- **Descendant selectors** `.a .b`

#### [[Multiple selectors] [A]](https://developer.mozilla.org/en-US/docs/Learn/CSS/Introduction_to_CSS/Combinators_and_multiple_selectors#Groups_of_selectors_on_one_rule)
This type of selectors enables applying the same rule to multiple selected elements at once.
```CSS
    h1, h2, h3, h4, h5, h6 {
        color: red;
    }
```

<br />

📚 **Useful resources:**
- 📃 [Type of Selectors | CSS Working Group](https://drafts.csswg.org/selectors-3/)
- 📃 [Taming Advanced CSS Selectors | Smashing Magazine](https://www.smashingmagazine.com/2009/08/taming-advanced-css-selectors/)

## Specificity [A-D]
Imagine you have this content structure
```HTML
    <header class='header_container'>
        <h1 id='mainTitle' class='title'>
            Title
        </h1>
    </header>
```
and this CSS
```CSS
    .title {
        color: blue;
    };
    h1 {
        color: red;
    };
    #mainTitle {
        color: green;
    };
```
### ❓ Will *`h1`* be `blue`, `red` or `green`?

Before answering this, you have to understand how to calculate `CSS specificity`.
The amount of specificity is measured by four numbers, let's call them `thousands`, `hundreds`, `tens`,and `ones`.
- **Thousands** - this number is applied with `inline styles`, and it's `0` (when there is no inline style) or `1`.
- **Hundreds** - each `id` (#)` selector adds score `1`.
- **Tens** - each `class`, `pseudo-class` or `attribute` selector adds score `1`.
- **Ones** - each `element` selector adds score `1`. 

The higher selector specificity number will always win, and style inside that selector will be applied to the selected content.

For better understanding, see how calculating specificity works in our example.


Selector | Thousands | Hundreds | Tens | Ones | Calculated Specificity in Our Example
------------ | --- | --- | --- | --- | ------
h1 | 0 | 0 | 0 | 1 | <span style='color: #2c8eef'>0001 </span>❌
.title | 0 | 0 | 1 | 0 | <span style='color: darkred'>0010 </span>❌
#mainTitle | 0 | 1 | 0 | 0 | **<span style='color: #42bb79'>0100</span> ✔️**
inline style | 1 | 0 | 0 | 0 | 0000 (not applied in our example)


As we can see from the table, calculated specificity is the highest for `#mainTitle` selector, so our **`h1`** text will be `green`.

> ⚠️ **Notes** 
>
> - Universal selector (*), combinators (+, >, ~, ' ') and negation pseudo-class (:not) have no effect on specificity.
>
> - If multiple selectors have the same importance and specificity, which selector wins is decided by which comes later in the Source order.
>
> - [`!important`](https://developer.mozilla.org/en-US/docs/Web/CSS/Specificity#The_!important_exception) - adding this after CSS value wins over everything, even an inline style.

<br />

📚 **Useful resources:**
- ❔  [**Codaxy Specificity Workshop**](https://codaxy-css-practice.netlify.app/specificity-game)
- 📃 [**CSS Specificity Wars | Stuff and Nonsense**](https://stuffandnonsense.co.uk/archives/css_specificity_wars.html) MUST SEE
- 📃 [How is Specificity Calculated? | MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/Specificity#The_!important_exception)
- 📃 [Cascade and Inheritance | MDN](https://developer.mozilla.org/en-US/docs/Learn/CSS/Introduction_to_CSS/Cascade_and_inheritance)
- 📃 [CSS Specificity: Things You Should Know | Smashing Magazine](https://www.smashingmagazine.com/2007/07/css-specificity-things-you-should-know/)
- ❔ [Specificity Quiz](https://mjswensen.github.io/css-power-ups/the-cascade-and-specificity/specificity-quiz/)


## [Inheritance] [B]
Some CSS properties are inherited from containers. For example, child element will have the same `color` and `font` as its container, if not specified otherwise.

<br />

📚 **Useful resources:**
- 📃 [List of Inherited CSS Properties | Git Repo](https://gist.github.com/dcneiner/1137601)
- 📃 [CSS Inheritance: An Introduction | Sitepoint](https://www.sitepoint.com/css-inheritance-introduction/)

## [Values] [A-E]
- Textual
    - Pre-defined values (flex-direction: `column`)
    - CSS-wide values (accepted by all CSS properties - `inherit`, `initial`, and `unset`)
    - URLs (absolute or relative)
- Numeric 
    - Integer [A]
    - Numbers [A]
    - Dimensions (`12px`, `1.2em`, `90deg`)
        - Distance 
            - Relative [A]: `em`, `%`, `vw`...
            - Absolute [A]: `px`, `cm`, `pt`,...
        - Angle [E]: `deg`, `grad`,...
        - Time [D]: `s`, `ms`
        - Frequency [E]: `Hz`, `kHz`
        - Resolution [E]: `dpi`, `dpcm`, `dppx`, `x`
    - Percentages [A]
    - Mixing percentages and dimensions [F]
- Color [C]
- Image [B]
- Position [C]
- Functional notation [D] (`calc()`, `min()`, `max()`,...)

<br />

📚 **Useful resources:**
- 📃 [CSS Values and Units | MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Values_and_Units)
- 📃 [CSS Values | W3 Resource](https://www.w3resource.com/css/CSS-values.php)
- 📃 [A Look at CSS Viewport Units](https://alligator.io/css/viewport-units/#:~:text=vh%20stands%20for%20viewport%20height,when%20the%20viewport%20is%20resized.)
- 📃 [HEX vs RGB vs HSL](https://blog.bitsrc.io/hex-vs-rgb-vs-hsl-what-is-the-best-method-to-set-css-color-property-f45d2debeee)
- 📃 [Make picking colors simple](https://bootcamp.uxdesign.cc/why-you-should-ditch-hex-and-use-hsl-to-make-picking-colors-easy-c376f69ae34e)

### [Shorthand Properties] [A-E]
Most common properties that are usually written shorthand:
- Border properties [A]
    ```CSS
    .bordered_container {
        /* shorthand */
        border-width: 1px;
        /* is the same as */
        border-top-width: 1px;
        border-right-width: 1px;
        border-bottom-width: 1px; 
        border-left-width: 1px;
    }
- Margin [A]
- Padding [A]
- Background [D]
- Font [D]
- Transition [E]

#### [Reading Shorthand] [A]
Shorthands handling properties related to edges of a box, like `border-width`, `margin` or `padding`, always use a consistent 1-to-4-value syntax representing those edges:

Shorthand | Reading |
---------------- | ------------------ | 
border-width: 2px; |![image](https://user-images.githubusercontent.com/17080238/155130439-a59bf765-ba2e-489f-ba7f-95ad82c7964c.png)| 
border-width: 2px 4px; | ![image](https://user-images.githubusercontent.com/17080238/155130309-348a59b2-62c7-4ac0-b0ae-25819c1f64d9.png)|
border-width: 2px 4px 6px; | ![image](https://user-images.githubusercontent.com/17080238/155130213-08d76b88-6ba1-436f-86ac-a47623326925.png) |
border-width: 2px 4px 6px 8px; (read clockwise)  | ![image](https://user-images.githubusercontent.com/17080238/155130115-b3f66841-45e2-4039-b794-9a7586ad4667.png)

*Images taken from [MDN]('https://developer.mozilla.org/en-US/docs/Web/CSS/Shorthand_properties')*

<br />

>⚠️ **Warning** 
>
> It's [not recommended](https://developer.mozilla.org/en-US/docs/Web/CSS/Shorthand_properties#Tricky_edge_cases) to use shorthands for more complicated properties, such as `background`. Use `background-color`, `background-image`, `background-size`... instead.

<br />

📚 **Useful resources:**
- 📃 [Shorthand Properties | MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/Shorthand_properties)

<br />

## Properties

When you begin with CSS, you probably start playing with properties that are easy to understand, colors - `color`, `background-color`, `border-color`, or fonts - `font-size`, `font-family`. And they usually work as expected.


The second step would probably be to modify `width`, `height`, `margin`, `padding`, and this is where most CSS beginners encounter their first frustrations. This is because they probably skipped one of the most important CSS concepts - `box model`.

### [Box Model] [A]
- width [A]
- height [A]
- padding [A]
- margin [A]
- border-width [A]
- box-sizing [A]
- background-clip [D]

The [`CSS box model`](https://developer.mozilla.org/en-US/docs/Learn/CSS/Introduction_to_CSS/Box_model) is the foundation of layout on the Web — each element is represented as a rectangular box, with the box's `content`, `padding`, `border`, and `margin` built up around one another like the layers of an onion.

<img src='./images/box-model.png' />

The layers are easy to understand, but what's usually causing confusion is `box-sizing` property.

#### [Box sizing] [A]
- content-box
- **border-box**

If a container has `width: 200px`, and also `padding: 20px` and `border-width: 4px`, it will 'grow' to  `248px` which equals 200px (*width*) + 2 * 20px (*left and right padding*) + 2 * 4px (*left and right border width*). This is because default `box-sizing` value is `content-box`.  

If we set `box-sizing: border-box`, the actual width will be the expected `200px`.

Box sizing behaviour is explained in these images.

<img src='./images/box-sizing-content.png' />
<img src='./images/box-sizing-border.png' />

>
>⚠️ **Note** 
> 
> `padding-box` is not used anymore.
>

<br />

📚 **Useful resources:**
- Box Model and Sizing
    - 📃 [Box Model | MDN](https://developer.mozilla.org/en-US/docs/Learn/CSS/Introduction_to_CSS/Box_model)
    - 📃 [Box Sizing | MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/box-sizing)
    - 📃 [Box Sizing | CSS Tricks](https://css-tricks.com/box-sizing/)
    - 📃 [Box Model | Learn Layout](https://learnlayout.com/box-model.html)

- Fonts
    - 📃 [Working with Typography | Shay Howe](https://learn.shayhowe.com/html-css/working-with-typography/)
- Colors
    - 📃 [CSS Color Module | CSS Working Group](https://drafts.csswg.org/css-color-3/)
    - 📃 [A Nerd’s Guide to Color on the Web | CSS Tricks](https://css-tricks.com/nerds-guide-color-web/)
    - 📃 [Color Value | MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/color_value)
- Background
    - 📃 [Background | MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/background)
    - 📃 [Background Position | CSS Tricks](https://css-tricks.com/almanac/properties/b/background-position/)
    - 📃 [Background Size | MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/background-size)
    - 📃 [Background Size | CSS Reference](https://cssreference.io/property/background-size/)

## Layout
Once you've understood how box model and `box-sizing` works, you're at least able to set absolute width and height of the element.

When it comes to CSS, the most common cause of problems is the **layout**. Element positioning, vertical or horizontal alignment, overflow, z-index can be hard to grasp for CSS beginners.

- Position
    - #### [static] [B]
    - #### [relative] [A]
    - #### [absolute] [A]
    - #### [fixed] [A]
    - #### [sticky] [D]
- Display
    - #### [inline] [A]
    - #### [inline-block] [A]
    - #### [block] [A]
    - #### [flexbox] [C]
    - #### [grid] [D]
    - #### [table] [D]
- [z-index] [C]
- [float] [D]
- [vertical-align] [A]
- [text-align] [A]

<br />

>
>⚠️ **Warning** 
> 
> [Do not use](https://stackoverflow.com/questions/9776840/are-floats-bad-what-should-be-used-in-its-place) `floats` for layout. "*They’re simply meant to take an element, put it to one side, and let other content flow around it. That’s all.*" Use `flexbox` and `grid` instead.

>*The float CSS property places an element on the left or right side of its container, allowing **text and inline elements** to wrap around it.* - MDN
>


Since it would take too long to explain how all these properties work, here are some learning resources.

<br />

📚 **Useful resources:**
- 📃 **[CSS Layout | Learn Layout](https://learnlayout.com/no-layout.html)**
- 📃 [Layout | Magic of CSS](https://adamschwartz.co/magic-of-css/chapters/2-layout/)

- Position

    - 📃 [Position | CSS Tricks](https://css-tricks.com/almanac/properties/p/position/)
    - 📃 [How to Use Position to Align Elements | Free Code Camp](https://www.freecodecamp.org/news/how-to-use-the-position-property-in-css-to-align-elements-d8f49c403a26/)
    - 📃 [Advanced Positioning | Interneting is Hard](https://internetingishard.com/html-and-css/advanced-positioning/)
    - 📃 [Sticky Postion | Elad Schechter](https://medium.com/@elad/css-position-sticky-how-it-really-works-54cd01dc2d46)
- Display

    - 📃 [Understanding CSS Display | Better Programming](https://medium.com/better-programming/understanding-css-display-none-block-inline-and-inline-block-63f6510df93)
    - 📃 [Visual Formatting Model | MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/Visual_formatting_model)
-  Flexbox

    - 📹 **[Flexbox Tutorial | Scrimba / Per Harald Borgen](https://scrimba.com/g/gflexbox)**
    - 📹 [Flexbox Tutorial | Wes Bos](https://flexbox.io/)
    - 📃 **[A Guide to Flexbox | CSS Tricks](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)**
    - 📃 [The Complete Illustrated Flexbox Tutorial | Free Code Camp](https://www.freecodecamp.org/news/the-complete-illustrated-flexbox-tutorial-d35c085dbf35/)
    - 📃 [Understanding Flexbox: Everything You Need To Know | Free Code Camp](https://medium.com/free-code-camp/understanding-flexbox-everything-you-need-to-know-b4013d4dc9af)
    - 🎮  [Flexbox Game | Flexbox Froggy](https://flexboxfroggy.com/)
- Grid
    - 📹 **[Grid Tutorial | Scrimba / Per Harald Borgen](https://scrimba.com/g/gflexbox)**
    - 📹 [Grid Tutorial | Wes Bos](https://courses.wesbos.com/account/access/5d41a44985f96c03c1e50f80)
    -  📐 [Learn CSS Grid | Griddy](https://griddy.io/)

- Z-index
    - 📃 [The Z-Index CSS Property: A Comprehensive Look | Smashing Magazine](https://www.smashingmagazine.com/2009/09/the-z-index-css-property-a-comprehensive-look/) 
    
## [Transition] [D]

Property `transition` is a shorthand for:
- `transition-property` (***all***, *color* , *box-shadow*, *background-color*, ...)
- `transition-duration` (*200ms*, *0.2s*, ...)
- `transition-timing-function` (***ease***, *linear*, *steps(4, end)*,  *cubic-bezier(0.4, 0.0, 1, 1)*, ...)
- `transition-delay` (*200ms*, *0.2s*, ...)


You can use both `transition` and `animation` property to add animation effect to an element.

The main difference between the two is that `transition` effect works only when an element changes its state (*:hover*, *:focus*, *:active*, ...), or when it's added to the page, or when it 'gets' or 'loses' a class. Also, `transition` only visualizes property change from a beginning state to an ending state.

For example, in material design, when you press a button (`:active` state), it seems like you're lifting it gradually. This effect is achieved by the `transition` property, which slowly changes button background-color and [box-shadow](https://css-tricks.com/almanac/properties/b/box-shadow/). 

```CSS
    .cxb-button {
        background-color: #f6f6f6;
        box-shadow: 0 1px 3px rgba(0, 0, 0, 0.45);

        transition: all 0.2s ease-out 0s;
        /*
            transition-porperty: all; (in this case, background-color and box-shadow)
            transition-duration: 0.2s;
            transition-timing-function: ease-out;
            transition-delay: 0s; (it's not necessary to set it to 0)
        */
        ...
    };
    .cxb-button:active {
        background-color: #eeeeee;
        box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);

        transition: all 0.2s ease-out 0s;
        /*
            transition-porperty: all; (in this case, background-color and box-shadow)
            transition-duration: 0.2s;
            transition-timing-function: ease-out;
            transition-delay: 0s; (it's not necessary to set it to 0)
        */
        ...
    };
```
<img src='./images/button-pressed-transition.gif' />

<br />

> 
> ⚠️ **Note**
>
> - You can't apply transition to all CSS properties. See the list of [animatable CSS properties](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_animated_properties).
>
> - **transition-delay: -400ms;** 
> You can use negative values for `transition-delay`: the transition will start as if it had already been playing for 400ms.

<br />

📚 **Useful resources:**
- 📃 **[Using CSS Transitions | MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Transitions/Using_CSS_transitions)**
- 📃 [Animatable CSS properties | MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_animated_properties)
- 📃 [transition-timing-function | CSS Tricks](https://css-tricks.com/almanac/properties/t/transition-timing-function/)
- 📃 [transition-timing-function | MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/transition-timing-function)
- 📃 [Advanced Transitions | Magic of CSS](https://adamschwartz.co/magic-of-css/chapters/6-transitions/)
- 📃 [Creative Link Effects | Tympanus](https://tympanus.net/Development/CreativeLinkEffects/)
- 📃 [Sidebar Transitions | Tympanus](https://tympanus.net/Development/SidebarTransitions/)

## [Animation] [D]
Unlike the effects set by `transition` property, `animation` effects don't need a trigger (hover, active,...) to run. They can happen automatically (on page load, for example).

Also, with `animation` you can set countless states between a start and an end state, or even loop animation. `transition` lets you style the appearance of an element only at the beginning of animation and at its end.

### When to use `animation`? 

If you need an animation to run when the page loads, or you have an animation more complex than a simple A to B state change, it is recommended to use the `animation` property.

[MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/animation) defines animations as *shorthand CSS property that applies an animation between styles*. It is a shorthand for:
- **animation-name**
- **animation-duration**
- **animation-timing-function**
- **animation-delay**
- animation-iteration-count
- animation-direction
- animation-fill-mode
-  animation-play-state

It is important to understand that you don't configure the actual animation effect with `animation` property. It is done with `@keyframes`. Once you define effects with `@keyframes`, you can assign them to a specific CSS element through `animation-name`.

```CSS
    .animated_container {
        height: 100px;
        background-color: red;
        animation: changeWidthSteps 3s ease-in 0s infinite;
        ...
        /*
            animation-name: changeWidthSteps;
            animation-duration: 3s;
            animation-timing-function: ease-in;
            animation-delay: 0s;
            animation-iteration-count: infinite;
        */
    };

    @keyframes changeWidthSteps {
        0% {
            width: 50px;
        }
        50% {
            width: 100px;
        }
        100% {
            width: 150px;
        }
    };

    /* if there are only two frames - 0% and 100%, you can also write it like this */
    @keyframes changeWidth {
        from {
            width: 50px;    
        }
        to {
            width: 150px;    
        }
    }
```

<img src='./images/animation.gif' />

<br />

📚 **Useful resources:**
- 📃 [Transitions VS Animations | CSS Animation Rocks](https://cssanimation.rocks/transition-vs-animation/)
- 📃 **[CSS Animation For Beginners | Thought Bot](https://thoughtbot.com/blog/css-animation-for-beginners)**
- 📃 [Advanced CSS Animation Property - animation-direction | MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/animation-direction)
- 📃 [Advanced CSS Animation Property - animation-fill-mode | MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/animation-fill-mode)
- 📃 [Advanced CSS Animation Property - animation-play-state | MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/animation-play-state)
- 📃 [A Simple CSS Animation Tutorial | FreeCodeCamp](https://www.freecodecamp.org/news/a-simple-css-animation-tutorial-8a35aa8e87ff/)
- 📃 [Material Design Motion | Google Material Design](https://material.io/design/motion/speed.html#easing)
- 📐 **[Best CSS Animation Library | Animista](http://animista.net/)**
- 📃 [Advanced Page Transition Examples | Tympanus](https://tympanus.net/codrops/2013/05/07/a-collection-of-page-transitions/)


## Transform [E]

[`CSS transforms`](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Transforms/Using_CSS_transforms) change the shape and position of the affected content **without disrupting normal document flow**.

You can transform elements with these properties:
- transform (***scale, rotate, translate***, *skew*)
- transform-origin (*used with transforms that need a specific point as a parameter - scale, rotate, skew, ...*)

or if you have a 3D object

- perspective [D]
- perspective-origin [D]

<br />

> ⚠️ **Notes** 
>
> Only elements positioned by the box model can be transformed. As a rule of thumb, an element is positioned by the box model if it has display: block.
>

<br />

📚 **Useful resources:**
- 📃 [Using CSS Transforms | MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Transforms/Using_CSS_transforms)
- 📃 **[Transform Values | CSS Reference](https://cssreference.io/property/transform/)**
- 📃 [Transform Origin | MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/transform-origin)
- 📃 **[Transform Origin | CSS Reference](https://cssreference.io/property/transform-origin/)**
- 📃 [Transform | CSS Tricks](https://css-tricks.com/almanac/properties/t/transform/)
- 📃 [3D Transforms | 24 Ways](https://24ways.org/2010/intro-to-css-3d-transforms/)


## Responsive Design [D]

- @media queries [B]
- **flexbox** [C]
- **css grid** [D]

When you hear `responsive design`, the first thing that comes to mind is probably `@media query`. However, since `flexbox` and `css grid` were introduced in 2015 and 2016-2017 (respectively), developers have more flexibility in implementing responsive designs.

Although it is now possible to create responsive layouts just with `flexbox` and `css grid`, it doesn't mean you should stop using `@media queries`. 
It is recommended to combine these two properties with media queries when creating responsive pages. 

1. Using only `@media queries` can be painful because you usually have to calculate widths of elements in %. You can end up with something a lot of unnecessary code:

```CSS
@media only screen and (min-width: 961px) {
    .card {
        width: 33.3%;
    }
};

@media only screen and (min-width: 401px) and (max-width: 960px) {
    .card {
        width: 50%;
    }
};

@media only screen and (max-width: 400px) {
    .card {
        width: 100%;
    }
};
```


2. Using only `flexbox` or `css grid` isn't always enough. Sometimes, you want the layout to behave in a specific way for mobile devices, but it can be difficult to achieve only with these two properties.
This is where `@media queries` become useful.
Take a look at this simplified example which [combines css grid with @media queries](https://thoughtbot.com/blog/concise-media-queries-with-css-grid) to quickly create flexible responsive layout.


<br />

📚 **Useful resources:**
- 📃 [Logic in Media Queries | CSS Tricks](https://css-tricks.com/logic-in-media-queries/)
- 📃 **[No Media Query Responsive Layout | CSS Tricks](https://css-tricks.com/look-ma-no-media-queries-responsive-layouts-using-css-grid/)**
- 📃 [Old Media Query Responsive Layout | Interneting is Hard](https://internetingishard.com/html-and-css/responsive-design/)
- 📃 [Responsive Design | Google](https://developers.google.com/web/fundamentals/design-and-ux/responsive/)
- 📃 **[Using Media Queries in 2018 | Smashing Magazine](https://www.smashingmagazine.com/2018/02/media-queries-responsive-design-2018/)**

<br/>

## Shapes [F]

## General CSS Guides and Tutorials
- 📃 [Learn CSS - Basic CSS and Applied Visual Design Sections | FreeCodeCamp](https://learn.freecodecamp.org/)
- 📃 [Introduction CSS | MDN](https://developer.mozilla.org/en-US/docs/Learn/CSS/Introduction_to_CSS)
- 📃 **[Most Common CSS Properties | CSS Reference](https://cssreference.io)**
- 📃 [CSS Quick Guide | Tutorials Point](https://www.tutorialspoint.com/css/css_quick_guide.htm)
- ❔ [CSS Quiz | Tutorialzine](https://tutorialzine.com/2017/07/how-well-do-you-know-css)
- ❔ [CSS Quiz | David Shariff](http://davidshariff.com/quiz/)


<br />

## CSS Variables
> 🚧 **This section will be available soon** 
>
>

## SCSS
- nesting [A]
- ampersand *&* [A]
- variables [A]
- interpolation [A]
- %placeholder [D]
- @ Rules
    - @import [A]
    - @extend [C]
    - @mixin [C]
    - @include [C]
    - @function [C]
    - @error [E]
    - @warn [E]
    - @debug [E]
    - @at-root [E]
- Flow Control [D]
    - @if and @else
    - @each
    - @for
    - @while
-  Values
    - numbers
    - strings
    - colors
    - lists [D]
    - maps [D]
    - true and false
    - null
- Built-In Funtions
    - plain CSS (*radial-gradient(red, blue)*) [D]
    - numbers (*abs, ceil, min*, ...) [B]
    - strings (*quote, str-index, str-insert*, ...) [D]
    - colors 
        - lighten, darken [A]
        - adjust-color, blue, desaturate, ... [D]
    - lists (*append, index, join*, ...) [E]
    - maps (*map-get, map-has-key, map-merge*, ...) [E]
    - selectors (*selector-extend*, ...) [E]

<br />

>⚠️ **Warning** 
>
> Combining SCSS and CSS variables
> -
>
> [SASS-lang](https://sass-lang.com/documentation/breaking-changes/css-vars): *To provide maximum compatibility with plain CSS, more recent versions of Sass require SassScript expressions in custom property values to be written within interpolation. Interpolation will also work for older Sass versions, and so is recommended for all stylesheets.* 
>
> See the image below.

<br />

<img src='./images/sass-and-css-variables.png' />

<br />

📚 **Useful resources:**
- 📃 **[SASS Documentation | SASS Lang](https://sass-lang.com/documentation)**
- 📃 [SASS Guidelines | Hugo Guiradel](https://sass-guidelin.es/)
- 📃 [SASS Basics | SASS Lang](https://sass-lang.com/guide)
- 📃 [Learn SASS in 15 Minutes | Toturialzine](https://tutorialzine.com/2016/01/learn-sass-in-15-minutes)
- 📃 [The SASS Ampersand | CSS Tricks](https://css-tricks.com/the-sass-ampersand/)
