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
- 


# Aligning Alibis

# Sizing Up the Properties

# Property Plotting

## Reference:
- [Flexbox Spec](http://go.codeschool.com/flebox-spec)
