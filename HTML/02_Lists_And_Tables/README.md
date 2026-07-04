# 02 — Lists and Tables

## Lists

A list in HTML is used to group related items together.  
HTML provides three types of lists — unordered, ordered, and definition.

---

### Unordered List

Used when the order of items does not matter.  
Renders with bullet points by default.

```html
<ul>
    <li>HTML</li>
    <li>CSS</li>
    <li>JavaScript</li>
</ul>
```

---

### Ordered List

Used when the order of items matters.  
Renders with numbers by default.

```html
<ol>
    <li>Wake up</li>
    <li>Study</li>
    <li>Practice</li>
</ol>
```

#### Ordered List Attributes

| Attribute | Purpose | Example |
|---|---|---|
| `type` | Changes the numbering style | `type="I"` `type="A"` `type="a"` `type="i"` |
| `start` | Sets the starting number | `start="5"` starts from 5 |
| `reversed` | Counts down instead of up | `reversed` |

```html
<!-- Roman numerals -->
<ol type="I">
    <li>HTML</li>
    <li>CSS</li>
    <li>JavaScript</li>
</ol>

<!-- Start from 5 and count down -->
<ol start="5" reversed>
    <li>Revise Notes</li>
    <li>Solve PYQs</li>
    <li>Practice Coding</li>
    <li>Take Mock Test</li>
    <li>Appear for Exam</li>
</ol>
```

> **Exam tip:** `reversed` is a boolean attribute — you write just the word, no value needed. `<ol reversed>` is correct. Writing `reversed="true"` is unnecessary.

---

### Nested Lists

A list placed inside another list item.  
Used to represent hierarchical or grouped information.

```html
<ul>
    <li>Programming Languages
        <ul>
            <li>C</li>
            <li>C++</li>
            <li>Python</li>
        </ul>
    </li>
    <li>Web Development
        <ol type="I">
            <li>HTML</li>
            <li>CSS</li>
            <li>JavaScript</li>
        </ol>
    </li>
</ul>
```

**Rules:**
- The nested list must be placed **inside** the `<li>` tag, not after it.
- You can mix `<ul>` and `<ol>` inside each other.
- Only `<li>` should be a direct child of `<ul>` or `<ol>`.

---

### Definition List

Used to display terms and their descriptions — like a glossary or dictionary.

```html
<dl>
    <dt>HTML</dt>
    <dd>HyperText Markup Language — the standard language for structuring web pages.</dd>

    <dt>CSS</dt>
    <dd>Cascading Style Sheets — used to control the visual presentation of HTML elements.</dd>

    <dt>JavaScript</dt>
    <dd>A programming language used to add interactivity and dynamic behaviour to web pages.</dd>
</dl>
```

| Tag | Full Name | Purpose |
|---|---|---|
| `<dl>` | Definition List | The container for the entire list |
| `<dt>` | Definition Term | The word or term being defined |
| `<dd>` | Definition Description | The description of the term above it |

> **Exam tip:** Definition lists are often forgotten by students but asked about in viva. They are semantically correct for FAQs, glossaries, and metadata pairs like "Author: John".

---

## Tables

A table in HTML is used to display **structured data** in rows and columns.

> **Most important rule in this entire section:**  
> Tables are for **data only** — never for page layout.  
> In the early days of web development, tables were misused to build entire page layouts (sidebars, headers, columns). This is now considered bad practice. CSS handles layout. HTML tables handle data.

---

### Basic Table Structure

```html
<table>
    <caption>Product Details</caption>
    <thead>
        <tr>
            <th scope="col">Product</th>
            <th scope="col">Price</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Laptop</td>
            <td>₹70,000</td>
        </tr>
        <tr>
            <td>Mouse</td>
            <td>₹500</td>
        </tr>
    </tbody>
    <tfoot>
        <tr>
            <td><strong>Total</strong></td>
            <td><strong>₹70,500</strong></td>
        </tr>
    </tfoot>
</table>
```

---

### Table Tags Explained

| Tag | Purpose |
|---|---|
| `<table>` | The container for the entire table |
| `<caption>` | The title of the table — placed immediately after `<table>` |
| `<thead>` | Groups the header rows — contains column labels |
| `<tbody>` | Groups the main data rows |
| `<tfoot>` | Groups the footer rows — used for totals or summaries |
| `<tr>` | Table Row — a single row inside any section |
| `<th>` | Table Header cell — bold and centred by default, carries semantic meaning |
| `<td>` | Table Data cell — regular data cell |

> **Exam tip:** `<thead>`, `<tbody>`, and `<tfoot>` are not just for organisation — they are semantic. Browsers can scroll `<tbody>` independently when printing long tables, and screen readers use these sections to understand the table structure.

---

### `colspan` and `rowspan`

Used to merge cells across columns or rows.

```html
<!-- colspan: merge across columns -->
<tr>
    <th colspan="3">My Family Members</th>
</tr>

<!-- rowspan: merge across rows -->
<tr>
    <td rowspan="2">Prachi</td>
    <td>HTML</td>
</tr>
<tr>
    <td>CSS</td>
</tr>
```

| Attribute | Merges across | Use case |
|---|---|---|
| `colspan="n"` | n columns horizontally | Group heading across multiple columns |
| `rowspan="n"` | n rows vertically | A cell that spans multiple rows |

---

### `scope` Attribute

The `scope` attribute is placed on `<th>` elements.  
It tells the browser and screen readers what the header applies to.

```html
<th scope="col">Name</th>    <!-- this header labels the column below it -->
<th scope="row">Total</th>   <!-- this header labels the row beside it -->
```

| Value | Meaning |
|---|---|
| `scope="col"` | Header applies to all cells in its column |
| `scope="row"` | Header applies to all cells in its row |

> **Exam tip:** `scope` is an accessibility attribute. Without it, a screen reader cannot tell which header belongs to which data cell. Always use it on `<th>` elements in a data table.

---

### What NOT to Do with Tables

```html
<!-- WRONG — using a table for layout -->
<table>
    <tr>
        <td>Sidebar content</td>
        <td>Main content</td>
    </tr>
</table>
```

This was common before CSS existed. It is now invalid practice.  
Tables must only be used when the data is genuinely tabular — rows, columns, and a relationship between them.  
For layout, use CSS Flexbox or Grid.

---

## Key Rules to Remember

| Rule | Why |
|---|---|
| Never use `border="1"` on a table | The `border` attribute is deprecated in HTML5 — use CSS instead |
| Never use a table for layout | Tables are for data, CSS is for layout |
| Always add `<caption>` | Gives the table an accessible, semantic title |
| Always use `scope` on `<th>` | Required for accessibility |
| Always separate `<thead>`, `<tbody>`, `<tfoot>` | Semantic structure — not optional for professional code |
| Only `<li>` as direct child of `<ul>` or `<ol>` | Any other tag directly inside breaks valid HTML |

---

## Files in This Folder

| File | Description |
|---|---|
| `index.html` | Practice page covering all list types and table structure |

---

## Common Viva / Exam Questions

**Q. What are the three types of lists in HTML?**  
A. Unordered list (`<ul>`), Ordered list (`<ol>`), and Definition list (`<dl>`).

**Q. What is the difference between `<th>` and `<td>`?**  
A. `<th>` is a table header cell — it is bold and centred by default and carries semantic meaning indicating it is a header. `<td>` is a regular data cell with no special meaning attached.

**Q. What does `colspan` do?**  
A. It merges a cell horizontally across a specified number of columns. For example, `colspan="3"` makes one cell span three columns.

**Q. What is `<tfoot>` used for?**  
A. It semantically groups the footer rows of a table — typically used for totals, summaries, or closing information. Browsers can render it independently when printing long tables.

**Q. Why should tables not be used for layout?**  
A. Tables create rigid, inaccessible, and unmaintainable structures when used for layout. Screen readers interpret tables as data grids, which causes confusion when the table is actually positioning content visually. CSS Flexbox and Grid are the correct tools for layout.

**Q. What is a definition list and when would you use it?**  
A. A definition list (`<dl>`) pairs terms (`<dt>`) with their descriptions (`<dd>`). It is semantically appropriate for glossaries, FAQs, dictionaries, and any key-value type content.

**Q. What is the `scope` attribute?**  
A. The `scope` attribute on a `<th>` element tells screen readers whether the header applies to its column (`scope="col"`) or its row (`scope="row"`). It is an accessibility requirement for data tables.

---

*Part of ITUE203 — Web Development Frameworks*  
*Topic: HTML → 02 Lists and Tables*