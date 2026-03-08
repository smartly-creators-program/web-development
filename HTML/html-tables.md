# HTML Tables

> Organize and display structured data clearly using HTML's powerful table elements.

---

## 📌 What is an HTML Table?

An HTML table is used to display **structured, relational data** in rows and columns — like a spreadsheet inside a webpage. Tables are ideal for things like pricing plans, schedules, comparison charts, and data reports.

> ⚠️ **Important:** Tables should be used for **tabular data only** — not for page layout. Use CSS Flexbox or Grid for layout instead.

---

## 🧱 Basic Table Structure

A table is built using a family of HTML elements that work together:

```html
<table>
  <tr>
    <th>Name</th>
    <th>Age</th>
    <th>City</th>
  </tr>
  <tr>
    <td>Alice</td>
    <td>24</td>
    <td>New York</td>
  </tr>
  <tr>
    <td>Bob</td>
    <td>30</td>
    <td>London</td>
  </tr>
</table>
```

### Output

| Name  | Age | City     |
|-------|-----|----------|
| Alice | 24  | New York |
| Bob   | 30  | London   |

---

## 🏷️ Core Table Elements

| Element | Description |
|---|---|
| `<table>` | The root container for the entire table |
| `<tr>` | Table Row — defines a horizontal row |
| `<th>` | Table Header — bold & centered by default |
| `<td>` | Table Data — a standard data cell |
| `<caption>` | A title/description shown above the table |

---

## 🗂️ Semantic Table Sections

For better structure, accessibility, and styling, split your table into three semantic sections:

```html
<table>
  <caption>Monthly Sales Report</caption>

  <thead>
    <tr>
      <th>Month</th>
      <th>Revenue</th>
      <th>Units Sold</th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>January</td>
      <td>$12,000</td>
      <td>240</td>
    </tr>
    <tr>
      <td>February</td>
      <td>$15,500</td>
      <td>310</td>
    </tr>
  </tbody>

  <tfoot>
    <tr>
      <td>Total</td>
      <td>$27,500</td>
      <td>550</td>
    </tr>
  </tfoot>
</table>
```

### Why use `<thead>`, `<tbody>`, `<tfoot>`?

| Section | Purpose |
|---|---|
| `<thead>` | Groups header rows — stays visible when scrolling long tables |
| `<tbody>` | Groups the main data rows |
| `<tfoot>` | Groups footer rows (totals, summaries) — renders last but can be declared anywhere |

---

## 🔗 Spanning Rows and Columns

Sometimes a single cell needs to span across multiple columns or rows.

### `colspan` — Merge across columns

```html
<table>
  <tr>
    <th colspan="3">Student Report Card</th>
  </tr>
  <tr>
    <th>Subject</th>
    <th>Score</th>
    <th>Grade</th>
  </tr>
  <tr>
    <td>Math</td>
    <td>92</td>
    <td>A</td>
  </tr>
</table>
```

The heading "Student Report Card" stretches across all 3 columns.

---

### `rowspan` — Merge across rows

```html
<table>
  <tr>
    <th>Day</th>
    <th>Session</th>
    <th>Topic</th>
  </tr>
  <tr>
    <td rowspan="2">Monday</td>
    <td>Morning</td>
    <td>HTML Basics</td>
  </tr>
  <tr>
    <td>Afternoon</td>
    <td>CSS Fundamentals</td>
  </tr>
</table>
```

"Monday" spans across two rows (Morning and Afternoon).

---

### Combining `colspan` and `rowspan`

```html
<table border="1">
  <tr>
    <th colspan="2" rowspan="2">Quarter Summary</th>
    <th>Q3</th>
    <th>Q4</th>
  </tr>
  <tr>
    <td>$40k</td>
    <td>$55k</td>
  </tr>
</table>
```

> 💡 **Tip:** Always count your cells carefully when using spans — mismatched cells will break the table layout.

---

## 🎨 Styling Tables with CSS

Raw HTML tables look plain. Here's how to make them look clean and readable:

```html
<style>
  table {
    width: 100%;
    border-collapse: collapse; /* removes double borders */
    font-family: Arial, sans-serif;
  }

  th, td {
    border: 1px solid #ddd;
    padding: 10px 14px;
    text-align: left;
  }

  th {
    background-color: #4a90e2;
    color: white;
  }

  tr:nth-child(even) {
    background-color: #f2f2f2; /* zebra striping */
  }

  tr:hover {
    background-color: #dceeff; /* highlight on hover */
  }
</style>
```

### Key CSS Properties for Tables

| Property | Description |
|---|---|
| `border-collapse: collapse` | Merges double borders into single borders |
| `border-spacing` | Controls gap between cells (when not collapsed) |
| `text-align` | Aligns text in cells (`left`, `center`, `right`) |
| `vertical-align` | Aligns content vertically in cells |
| `padding` | Adds space inside cells |
| `nth-child(even/odd)` | Creates alternating row colors (zebra stripes) |

---

## 📐 Column Styling with `<colgroup>` and `<col>`

Instead of styling each cell manually, use `<colgroup>` to apply styles to entire columns:

```html
<table>
  <colgroup>
    <col style="background-color: #fff9c4;">  <!-- Column 1 -->
    <col style="background-color: #c8e6c9;">  <!-- Column 2 -->
    <col style="width: 200px;">               <!-- Column 3 -->
  </colgroup>
  <tr>
    <th>Product</th>
    <th>Price</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>Laptop</td>
    <td>$999</td>
    <td>High-performance laptop</td>
  </tr>
</table>
```

> 💡 `<colgroup>` must be placed right after `<caption>` and before `<thead>`.

---

## ♿ Accessibility in Tables

Tables must be accessible to screen reader users. Here's how:

### Use `scope` on headers

```html
<table>
  <tr>
    <th scope="col">Name</th>
    <th scope="col">Score</th>
  </tr>
  <tr>
    <th scope="row">Alice</th>
    <td>95</td>
  </tr>
</table>
```

| `scope` value | Meaning |
|---|---|
| `col` | This header applies to its entire **column** |
| `row` | This header applies to its entire **row** |
| `colgroup` | Applies to a group of columns |
| `rowgroup` | Applies to a group of rows |

### Use `<caption>` for table titles

```html
<table>
  <caption>Top 5 Programming Languages in 2025</caption>
  ...
</table>
```

### Use `id` + `headers` for complex tables

```html
<th id="name">Name</th>
<td headers="name">JavaScript</td>
```

> ✅ **Best Practice:** Every table should have a `<caption>` and all `<th>` elements should use the `scope` attribute.

---

## 📊 Real-World Example: Comparison Table

```html
<table>
  <caption>Hosting Plan Comparison</caption>
  <thead>
    <tr>
      <th scope="col">Feature</th>
      <th scope="col">Basic</th>
      <th scope="col">Pro</th>
      <th scope="col">Enterprise</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">Storage</th>
      <td>5 GB</td>
      <td>50 GB</td>
      <td>500 GB</td>
    </tr>
    <tr>
      <th scope="row">Bandwidth</th>
      <td>100 GB</td>
      <td>Unlimited</td>
      <td>Unlimited</td>
    </tr>
    <tr>
      <th scope="row">Support</th>
      <td>Email</td>
      <td>Email & Chat</td>
      <td>24/7 Priority</td>
    </tr>
    <tr>
      <th scope="row">Price/mo</th>
      <td>$5</td>
      <td>$20</td>
      <td>$99</td>
    </tr>
  </tbody>
</table>
```

---

## 🧠 Key Takeaways

- Use `<table>`, `<tr>`, `<th>`, and `<td>` as the core building blocks of any table.
- Always use **`<thead>`, `<tbody>`, `<tfoot>`** for semantic structure and better styling control.
- Use **`colspan`** to merge cells horizontally and **`rowspan`** to merge cells vertically.
- Apply **`border-collapse: collapse`** in CSS for clean, single-line borders.
- Always add **`<caption>`** and **`scope`** attributes for accessibility.
- Never use tables for **page layout** — that's what CSS Grid and Flexbox are for.

---
