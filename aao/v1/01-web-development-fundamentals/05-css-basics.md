# CSS

## Selectors

- Type selectors -- matches elements by node name `div, li, a, p`
- Class selectors -- matches elements by class name `<button class=“active”>`
- ID selectors -- matches elements by ID name `<div id=”list-1”>`
- Universal selectors -- matches elements of any type `\*`
- Attribute selectors -- matches elements based on the presence or value of a given attribute (e.g. `a[title]` matches all a elements with a title attribute)

One rule, many selectors

```css
h1,
h2 {
  font-style: italic;
}
```

Get more granular with multiple selectors on one rule

```css
h1#heading,
h2.subheading {
  font-style: italic;
}
```

### Descendant Selectors

Separate selectors by only white space (i.e. no commas) and it will treat the second as a descendant of the first.

> Selects all abbr elements contained in p elements

```css
p abbr {
  text-transform: uppercase;
}
```

### Direct Child Selector

Matches every element `b` that is directly inside `a`.

```css
.a > .b {
  background-color: #ffe0b2;
}
```

### Adjacent Sibling Selectors

Matches when two elements share the same parent, and the second comes directly after the first.

Here, we are selecting H2's that immediately proceed after an H2. (It doesn't select the H1.)

```css
h1 + h2 {
  font-style: italic;
}
```

### Pseudo-class

Specifies a special state of the selected element(s) and does not refer to any elements or attributes contained in the DOM.

```css
a:hover {
  color: #4fc3f7;
}
```

Pseudo-classes

- `active`: applies to elements like buttons when activated by a person, like when they "push down" on the button
- `checked`: applies to radio inputs, checkbox inputs, and options in drop downs when the user has toggled it into an "on" state
- `disabled`: applies to any disabled element, like a disabled button or input
- `first`-child: applies to the first element among a group of sibling elements
- `focus`: applies to elements that have the current focus, like inputs and buttons
- `hover`: applies to elements that currently have the pointing device (cursor) directly over it (it is problematic on touchscreens because it may never match the element because there is no persistent pointing device)
- `invalid`: applies to any form element in an invalid state due to client-side form validation
- `last-child`: applies to the last element among a group of sibling elements
- `not(selector)`: represents elements that do not match the provided selector
- `required`: applies to form elements that are required
- `valid`: applies to any form element in a valid state
- `visited`: applies to anchor tags of which the user has already been to the URL that the href points to

```

Pseudo-selectors
Like pseudo-classes, pseudo-selectors select pseudo elements in the DOM. That's kind of weird, pseudo elements. The two that you will use most often are the `::after `and the `::before` pseudo-selectors. Both of them create a pseudo-element as a child of the element to which the property applies. The `::after` variation creates the child as the last child of the selected element. The `::before` variation creates the child as the first child of the selected element.

```
