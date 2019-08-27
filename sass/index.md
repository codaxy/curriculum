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

#### [BOX MODEL] [A]
- `width`
- `height`
- `padding`
- `border`
- `margin`

#### [POSITIONING] [AD]
- `static` [B]
- `relative` [A]
- `absolute` [A]
- `fixed` [A]
- `sticky` [D]
- `z-index` [C]
- `float` [A]
- `vertical-align` [A]
- `text-align` [A]

#### [DISPLAY] [AD]
- `inline` [A]
- `inline-block` [A]
- `block` [A]
- `flexbox` [C]
- `grid` [D]
- `table` [D]

## Animations
#### [TRANSITION] [C]
#### [ANIMATION] [D]
#### [TRANSFORM] [E]

##  Responsive design
#### [MEDIA QUERIES] [B]
#### [FLEXBOX] [C]
#### [CSS GRID] [D]

## Conventions
#### [STYLING-CONV] [A]

- [Codaxy CSS Conventions](css-conventions.md)
