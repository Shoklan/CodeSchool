# Adventures in Web Animations
## Alyssa Nicoll


# Transitions
- We guide users using color, font and motion.
- Transitions delay the state change over time.
- A **Primary Call To Action**, or CTA, is the primary goal for a user.
- You can control the color using `.btn:hover`.
- Make sure to keep the transitions subtle unless it's exceptionally important.
- The format for a transition is `transition: <property> <duration>;`
- This attribute is added to the original class.
- The fastest transition a human eye can handle is .2565.
- You can chain trainsitions using a comma: `background-color .4s, color .4s;`.
- You can also just add `all` but that will transition every property that is able.
- There is actually four values to the full formula: `trainsition: <property> <duration> <timing-function> <delay>;`.
- **Vendor Prefixes** include:
  * -webkit-transition: ...
  * -moz-transition: ...
  * -ms-transition: ...
  * -o-transition: ...
- You can use the website [CanIUse](www.caniuse.com) to check compatability issues.
- To create alternating text on hover:
  1. Create two inner spans; one per content.
  2. Style both states of the btn.
  3. Create a transition between states.
- **Absolute** means position me according to my nearest positioned parent or document.

```css
.btn{ position: relative;}
.content{ position: absolute;}

.top{ top: 0;}
.bottom{ top: 100px;}

.btn:hover .top{ top: -100px;}
.btn:hover .bottom{ top: 0px;}

.content{
  position: relative;
  transition: top .03s;
  overflow: hidden;
}
```
- There are three parts:
  1. the modal header
  2. the modal content
  3. the modal overlay
```css
.modal,
.modal-overlay{
  visibility: hidden;
  opacity: 0;
}

.modal.active,
.modal-overlay.active{
  opacity: 1;
  visibility: visible;
}
```
- We can't use `display: none` because it can't be transitioned.
- We can tell an element will be able to transition when there is a middle state.


# Transforms
- **CSS Transforms** let you modify elements in their coordinate space.
- Rotation is as simple as `.modal-close:hover{ transform: rotate(360deg);}`.
- Don't forget to tag the original element with the `transition` element.
- The full list of timing functions:
  1. ease
  2. linear
  3. ease-in
  4. ease-out
  5. initial
  6. inherit
  7. ease-in-out
  8. cubic-bezier
- `.form-input + .form-label` for future reference.
- `+` is called the **Adjacent Selector**.
- **Scale** is used to stretch an element basedon the vlaue multiplier.
- To do that, `transform: scale( 2, 1 )`.
- You can adjust where the element scales to using `transform-origin: center left;`.
- To simply move an element independent of all other elements use `transform: translateX(<n>px);`.
- `:focus` is an important selector to keep in mind.

# Keyframes
- **Keyframes** are a list of what should happen over the course of the animation.
- There are two parts:
  1. Create the animation.
  2. Assign the animation.
- Formula:
```css
@keyframes <name-animation> {
  <step 1> {<property>: <value>;}
  <step 2> {<property>: <value>;}
  }
```
- Make sure each piece is separate.
- You'll tag each id with `#left-arm{ animation: swing 2s 0 infinite ease;}`.
- *Duration must come before delay.*
- Don't forget about `transform-origin: top center;`.
- To make animations smoother, you simply add more steps.
- You can condense duplicate values in *keyframes* and put them on one line.
- The default **Fill Mode** is none.
- To keep it up, you'd use `forwards` instead.
- What is a **Cubic-Bezier**>
- It's a curve that tells you how fast something changes over time.
- All timing functions are *cubic-bezier* functions that are well defined.

# SVG
- There are lots of animation that are simply impossible without SVG.
- You can create SVGs in *Adobe Illustrator*.
- The parts of an SVG contain ids you can reference.
- You can insert SVGs in place of PNGs in html.
- SVGs, or Scalable Vector Graphics - can be scaled to any size.
- You can check the full list of svg properties [here](http://go.codeschool.com/svg-css-properties).

## References:
- [CanIUse](www.caniuse.com)
- [SVG Properties](http://go.codeschool.com/svg-css-properties)

## Research:
- [CSS-Tricks](http://CSS-tricks.com)
- [Cubic-Bezier](http://cubic-bezier.com)
- [pleease](http://pleeease.io)
