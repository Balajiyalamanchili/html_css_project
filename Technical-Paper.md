# HTML & CSS Essentials

## The CSS Box Model Explained

Understanding the CSS box model is crucial for effective web page layout and design. The box model treats every HTML element as a box, made up of several layers that determine its size and spacing on the page.

### Box Model Layers

Each element consists of four main layers, from innermost to outermost:

1. **Content**  
  The area where your text, images, or other media appear. Controlled by the `width` and `height` properties.

2. **Padding**  
  The transparent space between the content and the border. Padding can be set for each side individually (e.g., `padding-left`, `padding-bottom`).

3. **Border**  
  Surrounds the padding and content. Borders can have different widths, styles, and colors, and can be customized per side (e.g., `border-top`).

4. **Margin**  
  The outermost transparent space that separates the element from others. Margins are always transparent and can be set individually.

### Calculating Total Size

By default, the `width` and `height` properties define only the content area. The total space an element occupies is:

```
Total width = width + left/right padding + left/right border + left/right margin
Total height = height + top/bottom padding + top/bottom border + top/bottom margin
```

> **Note:** Margins add space outside the border but are not included in the element’s total width/height as calculated by the browser.

#### Example

```css
.box {
  width: 300px;
  height: 100px;
  padding: 20px;
  border: 5px solid #000;
  margin: 15px;
  background: #add8e6;
}
```

#### `box-sizing` Property

By default, CSS uses `box-sizing: content-box`, so width/height apply only to the content.  
Set `box-sizing: border-box` to include padding and border within the specified width and height, simplifying layout.

---

## Inline vs Block Elements

HTML elements are either **block-level** or **inline** by default, affecting how they appear and interact on the page.

### Block-Level Elements

- Begin on a new line
- Stretch to fill the container’s width
- Can contain other block or inline elements

**Common block elements:**

```html
<div>...</div>
<p>...</p>
<h1>...</h1>
<ul>...</ul>
<li>...</li>
<section>...</section>
<header>...</header>
<footer>...</footer>
```

**Example:**

```html
<p>Paragraph one.</p>
<div>Block-level div.</div>
```
These will appear on separate lines.

### Inline Elements

- Do not start on a new line
- Only take up as much width as needed
- Can contain text or other inline elements

**Common inline elements:**

```html
<span>...</span>
<a href="#">...</a>
<strong>...</strong>
<em>...</em>
<img src="..." />
<code>...</code>
```

**Example:**

```html
<p>This is <strong>bold</strong> and <em>italic</em> text.</p>
```
Inline elements flow within the surrounding text.

#### Changing Display Type

You can override the default display using CSS:

```css
div { display: inline; }
span { display: block; }
```

---

## CSS Positioning: Relative vs Absolute

The `position` property controls how elements are placed in the document.

### `position: relative`

- Element is offset relative to its normal position
- Still occupies its original space in the layout

**Example:**

```css
.relative-box {
  position: relative;
  top: 20px;
  left: 30px;
}
```

### `position: absolute`

- Positioned relative to the nearest ancestor with a position other than `static`
- Removed from the normal flow (does not reserve space)
- If no ancestor is positioned, it’s relative to the `<html>` or `<body>`

**Example:**

```css
.container { position: relative; }
.tooltip {
  position: absolute;
  top: 100%;
  left: 0;
}
```

> **Tip:** Use `absolute` inside a `relative` container for precise placement.

---

## Common CSS Utility Classes

**Structural:**
- `.container`, `.row`, `.col`, `.wrapper`, `.section`, `.header`, `.footer`, `.main`, `.aside`, `.content`, `.nav`, `.card`

**Styling:**
- `.text-center`, `.text-left`, `.text-right`
- `.bg-light`, `.bg-dark`, `.bg-primary`
- `.btn`, `.btn-primary`, `.btn-secondary`
- `.rounded`, `.rounded-full`
- `.shadow`, `.shadow-lg`
- `.m-0`, `.m-1`, `.m-auto` (margin)
- `.p-0`, `.p-1`, `.p-auto` (padding)
- `.d-block`, `.d-inline`, `.d-flex`
- `.hidden`, `.visible`
- `.border`, `.border-0`, `.border-primary`

---

## CSS Specificity

Specificity determines which CSS rule applies when multiple rules target the same element.

### How Specificity Works

Specificity is calculated as a four-part value: **(a, b, c, d)**

- **a:** Inline styles (`style=""`)
- **b:** Number of ID selectors (`#id`)
- **c:** Number of class, attribute, and pseudo-class selectors (`.class`, `[attr]`, `:hover`)
- **d:** Number of element and pseudo-element selectors (`div`, `::before`)

The higher the value, the more specific the rule.

**Examples:**

| Selector                  | Specificity | Notes                        |
|---------------------------|-------------|------------------------------|
| Inline style              | (1,0,0,0)   | Highest                      |
| `#main`                   | (0,1,0,0)   | ID selector                  |
| `.item`                   | (0,0,1,0)   | Class selector               |
| `[type="text"]`           | (0,0,1,0)   | Attribute selector           |
| `:hover`                  | (0,0,1,0)   | Pseudo-class                 |
| `div`                     | (0,0,0,1)   | Element selector             |
| `::after`                 | (0,0,0,1)   | Pseudo-element               |
| `*`                       | (0,0,0,0)   | Universal selector           |

---

## Responsive Design with Media Queries

Media queries let you apply styles based on device characteristics.

**Common breakpoints:**
- `max-width: 576px` — mobile
- `577px - 768px` — tablet
- `769px - 992px` — small desktop
- `993px - 1200px` — large desktop
- `min-width: 1201px` — extra large screens

---

## Flexbox & Grid Layouts

### Flexbox

A one-dimensional layout system for arranging items in a row or column.

- `display: flex;` — enables flex context
- `flex-direction` — row or column
- `justify-content` — horizontal alignment
- `align-items` — vertical alignment
- `flex-wrap` — wrapping behavior
- `flex-grow`, `flex-shrink`, `flex-basis` — item sizing

### Grid

A two-dimensional layout system for rows and columns.

- `display: grid;` — enables grid context
- `grid-template-columns` / `grid-template-rows` — define structure
- `gap` — spacing between items
- `grid-column` / `grid-row` — item placement
- `justify-items` / `align-items` — alignment
- `grid-template-areas` — named areas

> Use Flexbox for simple, one-direction layouts; use Grid for complex, two-dimensional layouts.

---

## Essential HTML Meta Tags

Meta tags go inside the `<head>` and provide metadata for browsers and search engines.

| Meta Tag Example                                      | Purpose                                      |
|-------------------------------------------------------|----------------------------------------------|
| `<meta charset="UTF-8">`                              | Character encoding (supports all languages)  |
| `<meta name="viewport" content="width=device-width, initial-scale=1.0">` | Responsive design for mobile devices         |
| `<meta http-equiv="X-UA-Compatible" content="IE=edge">` | Use latest IE rendering engine               |
| `<meta name="description" content="...">`             | SEO summary for search engines               |
| `<meta name="keywords" content="HTML, CSS, ...">`     | (Legacy) keywords for search engines         |
| `<meta name="author" content="Your Name">`            | Author information                           |

**Why use these?**  
They ensure your site displays correctly, is discoverable, and provides important info to browsers and search engines.

---

