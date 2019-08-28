# Styling, SASS and CSS

# CSS

#### [Guide] [B]
- [CSS Guide](css-guide.md)

#### [INSERTING CSS] [A]
- Inline
- Internal
- External
- External using @import

#### [SYNTAX] [A]
- [Selector](#SELECTORS)
- Declaration
- [Property](#PROPERTIES)
- [Value](#VALUES)

## SELECTORS
#### [SIMPLE SELECTORS] [A]
- type
- class
- id
#### [PSEUDO SELECTORS] [A]
- `:hover`
- `:focus`
- `:active`
- `:not()`
- `:first-child`
- `:last-child`
- `:nth-child()`
#### [PSEUDO ELEMENTS] [D]
- `:after`
- `:before`
- `:first-line`
#### [ATTRIBUTE SELECTORS] [D]
- `[attr]`
- `[attr=value]`
- `[attr~=value]`
- `[attr|=value]`
- `[attr^=value]`
- `[attr$=value]`
- `[attr*= ]`
#### [COMBINATORS] [C]
- `.a + b.`
- `a. ~ b.`
- `a. > b.`
- `a. b.`
#### [MULTIPLE] [A]

<br />

#### [SELECTOR SPECIFICITY] [AD]
- Inline style specificity
- Id selector specificity
- Class selector specificity
- Pseudo class selector specificity
- Attribute selector selector specificity
- Source order specificity
- !important
- Universal, combinators, and negation pseudo-class selector specificity

## Values
#### [TEXTUAL] [C]
- Pre-defined values
- CSS-wide values 
- URLs (absolute or relative)
#### [NUMERIC] [AF] 
- Integer [A]
- Numbers [A]
- Dimensions
    - Distance 
        - Relative [A]
        - Absolute [A]
    - Angle [E]
    - Time [D]
    - Frequency [F]
    - Resolution [E]
- Percentages [A]
- Mixing percentages and dimensions [F]
#### [COLOR] [A]
- keywords `red`
- hex `#000000`
- `rgb`
- `hsl`
- `transparent`
- `currentColor`
#### [IMAGE] [B]
#### [POSITION] [C]
- top
- right
- bottom
- left
#### [FUNCTIONAL NOTATION] [D]
- `url()`
- `calc()`
- `var()`
- `hsl()`
- `rgb()`
- `linear-gradient()`
- `cubic-bezier()`
- `max()`
- `min()`

## Properties
#### [MOST COMMON PROPERTIES] [A]
- `color`
- `background-color`
- `border`
- `font-size`
- `font-weight`
- `margin`
- `padding`
- `width`
- `height`

#### [SHORTHAND PROPERTIES] [AE]
- `border` properties [A]
- `margin` [A]
- `padding` [A]
- `background` [C] 
- `font` [D]
- `transition` [D]
- `animation` [E]

#### [TYPOGRAPHY] [A]
- `color`
- `font`
    - `font-family`
    - `font-size`
    - `font-weight`
- `text-align`
- `text-decoration`
- `text-transform`
- `white-space`
- `text-overflow`

#### [BACKGROUND] [AD]
- `background-color` [A]
- `background-image` [A]
- `background-position` [B]
- `background-repeat` [A]
- `background-attachment` [D]
- `bacgkround-size` [C]
- `background-position` [B]
- `background-origin` [D]

#### [BOX MODEL] [A]
- `width`
- `height`
- `padding`
- `border`
- `margin`
- `line-height`
- **`box-sizing`**

#### [POSITIONING] [AD]
- `position`
    - `static` [B]
    - `relative` [A]
    - `absolute` [A]
    - `fixed` [A]
    - `sticky` [D]
- `z-index` [C]
- `float` [A]
- `vertical-align` [A]
- `text-align` [A]
- `top` [A]
- `right` [A]
- `bottom` [A]
- `left` [A]

#### [DISPLAY] [AD]
- `inline` [A]
- `inline-block` [A]
- `block` [A]
- `flexbox` [C]
- `grid` [D]
- `table` [D]


### Animations
#### [TRANSITION] [C]
- `transition-property`
- `transition-duration`
- `transition-timing-function`
- `transition-delay`

#### [ANIMATION] [D]
- `animation-name`
- `animation-duration`
- `animation-timing-function`
- `animation-delay`
- `animation-iteration-count`
- `animation-direction`
- `animation-fill-mode`
- `animation-play-state`

#### [TRANSFORM] [E]
- `transform`
    - `scale`
    - `translate`
    - `skew`
    - `rotate`
- `transform-origin`


##  Responsive design
#### [MEDIA QUERIES] [B]

#### [FLEXBOX] [C]
- Container
    - `flex-direction`
    - `flex-wrap`
    - `justify-content`
    - `align-items`
    - `align-content`
- Items
    - `flex`
        - `flex-grow`
        - `flex-shrink`
        - `flex-basis`
    - `align-self`
    - `order`

#### [CSS GRID] [D]
- Container
    - `grid-template`
        - `grid-template-rows`
        - `grid-template-columns`
    - `grid-template-areas`
    - `grid-gap`
    - `grid-auto-columns`
    - `grid-auto-flow`
    - `grid-auto-rows`
    - `justify-content`
    - `align-items`
    - `align-content`
- Items
    - `grid-area`
    - `grid-column`
    - `grid-row`
    - `align-self`


## SCSS

#### [GENERAL] [A]
- nesting
- ampersand *&*
- variables 
- interpolation 
- % placeholder

#### [@ Rules] [AE]
- @import [A]
- @extend [B]
- @mixin [C]
- @include [C]
- @function [D]
- @error [E]
- @warn [E]
- @debug [E]
- @at-root [E]

#### [FLOW CONTROLE] [D]
- @if and @else
- @each
- @for
- @while

#### [VALUES] [AD]
- numbers [A]
- strings [A]
- colors [A]
- lists [D]
- maps [D]
- true and false [A]
- null

#### [BUILT-IN FUNCTIONS] [AE]
- plain CSS (*radial-gradient(red, blue)*) [D]
- numbers (*abs, ceil, min*, ...) [B]
- strings (*quote, str-index, str-insert*, ...) [D]
- colors 
    - lighten, darken [A]
    - adjust-color, blue, desaturate, ... [D]
- lists (*append, index, join*, ...) [E]
- maps (*map-get, map-has-key, map-merge*, ...) [E]
- selectors (*selector-extend*, ...) [E]

## Conventions
#### [STYLING-CONV] [A]

- [Codaxy CSS Conventions](css-conventions.md)
