# Cracking the Case With FlexBox
## Dan Denney

# Foreshadowing Flexbox
- **Flexbox** is a collection of CSS properties used to align content and distribute space.
- Flex is a new display layout.
- The bulk of the impact is actually from changing the parent element.
- `display: flex;` will fill up as much space as it can.
- `display; inline-flex;` will take up as much space as the internal elements.
- Flex will not have any impact on grandchildren so you can control the grouping using divs.
- There is a `flex-wrap` property which defaults to *nowrap*.
- It can also have the values:
  1. wrap
  2. wrap-reverse
- Sometimes you always want flex to be active.
- You can control this using the `flex-direction` property.
- It can have the values:
  1. row
  2. row-reverse
  3. column
  4. column-reverse
- You can even treat the whole page as a flex element.
- You can control size specific wraping using:
```css
@media screen and (min-width: 500px) {

  .media{
    flex-wrap: nowrap;
  }

  .media-img-item {
    width: 200px;
  }

}
```
- These will override the normal settings.

# Justification and Order
- Flex items are distributed along flex axis.
- The main axis is determined by `flex-direction`.
- You can control the side items justify to using `justify-content`.
- It has the values:
  1. `flex-start`
  2. `flex-end`
  3. `space-between`
  4. `space-around`
  5. `center`; default
- The `order` property is used to determine the order of flex items along the main axis.
- This sort of works kind of like z axis marked elements.

# Aligning Alibis
- Flex items are also aligned on the **Cross Axis**.
- Property `align-items` is used to distribute space on the *cross axis*.
- It has the values:
  1. stretch
  2. flex-start
  3. flex-end
  4. center
  5. baseline

# Sizing Up the Properties
- Worth noting: overriding Chromes `min-width: 0;` to fix compatability issues.
- The property `flex-grow` is used to specify the ratio of the space and item should fill in the main axis.
- If we set it to 0 then it wont grow.
- If we set it to 1 then it will fill all the space available.
- The ratio has to account for the elemens internal to it; don't depend on it too much.
- The property `flex-shrink` will control how much an item is willing to scale down to fit.
- If we set it to 0 then it wont shrink.
- The property `flex-basis` can be used to set the initial size of a flex item.
- It can take the units:
  1. percent.
  2. px
  3. em
  4. rem

# Property Plotting
- The property `align-self` is used to override the items parent settings.
- It accepts the values:
   1. stretch
   2. flex-start
   3. flex-end
   4. center
   5. baseline
- A simple way to center and max is `flex-wrap: center; flex-basis: 100%;`.
- `align-items` does not control wrapped items.
- The property `align-content` is used to align wrapped flex items.
- It accepts the values:
  1. flex-start
  2. flex-end
  3. center
  4. space-between
  5. space-around
- The property for flex shorthand is `flex: <grow> <shrink> <basis>;`.
- If you **REALLY** need to support Internet Explorer, then don't use the shorthand.
- The property `flex-flow: <direction> <wrap>;` is used for shorthand direction setting.

## Reference:
- [Flexbox Spec](http://go.codeschool.com/flebox-spec)
- [Flexbox Froggy](www.flexboxfroggy.com)
