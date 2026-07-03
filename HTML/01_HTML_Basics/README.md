# 01 — HTML Basics

## What is HTML?

HTML stands for **HyperText Markup Language**.  
It is the standard language used to create the structure of web pages.

- **HyperText** means text that contains links to other pages.
- **Markup Language** means we use tags to annotate and structure content.

HTML is **not** a programming language. It does not have logic, loops, or conditions.  
It only defines **what is on the page**, not how it looks (CSS) or how it behaves (JavaScript).

---

## HTML Document Structure

Every HTML file must follow this base structure:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Page Title</title>
  </head>
  <body>
    <!-- Page content goes here -->
  </body>
</html>
```

### Breaking it down

| Tag / Declaration | Purpose |
|---|---|
| `<!DOCTYPE html>` | Tells the browser this is an HTML5 document |
| `<html lang="en">` | Root element of the page. `lang` helps screen readers and search engines |
| `<head>` | Contains metadata — information about the page, not visible to the user |
| `<meta charset="UTF-8">` | Sets character encoding. UTF-8 supports all languages and symbols |
| `<meta name="viewport" ...>` | Makes the page responsive on mobile devices |
| `<title>` | Sets the text shown on the browser tab |
| `<body>` | Contains all visible page content |

> **Exam tip:** `<!DOCTYPE html>` is a declaration, not a tag. It has no closing tag and tells the browser to render the page in standards mode, avoiding quirks mode.

---

## Headings

HTML has six levels of headings, `<h1>` through `<h6>`.

```html
<h1>Main Heading</h1>
<h2>Section Heading</h2>
<h3>Sub-section</h3>
<h4>Sub-sub-section</h4>
<h5>Minor Heading</h5>
<h6>Smallest Heading</h6>
```

**Rules:**
- Use only **one `<h1>`** per page — it represents the main topic.
- Do not skip levels (e.g., do not jump from `<h1>` to `<h4>`).
- Headings define **document outline**, not just visual size.

> **Exam tip:** Headings are important for SEO (Search Engine Optimization) and accessibility. Screen readers use heading hierarchy to navigate a page.

---

## Paragraphs

```html
<p>This is a paragraph of text.</p>
```

- Each `<p>` tag creates a block of text with automatic spacing above and below.
- Browsers ignore extra spaces and line breaks inside HTML — use tags instead.

---

## Line Break and Horizontal Rule

```html
<p>First line.<br />Second line in the same paragraph.</p>

<hr />
```

| Tag | Purpose |
|---|---|
| `<br>` | Inserts a line break without starting a new paragraph |
| `<hr>` | Inserts a horizontal dividing line — used to separate sections |

> Both are **void elements** — they have no closing tag.

---

## Comments

```html
<!-- This is a comment and will not appear on the page -->
```

- Used to leave notes in code for yourself or other developers.
- Not visible to users in the browser but **visible in page source** — never put sensitive information in comments.

---

## Text Formatting Tags

```html
<strong>Important text</strong>       <!-- Bold + semantic importance -->
<em>Emphasized text</em>              <!-- Italic + semantic emphasis -->
<b>Bold text</b>                      <!-- Bold, no semantic meaning -->
<i>Italic text</i>                    <!-- Italic, no semantic meaning -->
<u>Underlined text</u>
<s>Strikethrough text</s>
<mark>Highlighted text</mark>
<small>Small print text</small>
<sup>Superscript</sup>                <!-- e.g. x² -->
<sub>Subscript</sub>                  <!-- e.g. H₂O -->
```

> **Exam tip — important distinction:**
> - `<strong>` and `<em>` are **semantic** tags. They carry meaning — screen readers will stress `<em>` text when reading aloud.
> - `<b>` and `<i>` are **presentational** tags. They only change appearance with no added meaning.
> - In modern HTML, prefer `<strong>` over `<b>` and `<em>` over `<i>`.

---

## Preformatted Text

```html
<pre>
  This    text
      preserves   spacing
  and line breaks exactly.
</pre>
```

- The `<pre>` tag displays text in a monospace font and respects all whitespace and line breaks.
- Commonly used to display code blocks.

---

## Links

```html
<a href="https://www.example.com" target="_blank" title="Visit Example">Click here</a>
```

| Attribute | Purpose |
|---|---|
| `href` | The URL the link points to |
| `target="_blank"` | Opens the link in a new tab |
| `title` | Tooltip text shown on hover |

**Types of links:**

```html
<!-- External link -->
<a href="https://google.com">Google</a>

<!-- Internal link (another page in same project) -->
<a href="about.html">About Me</a>

<!-- Link to a section on the same page -->
<a href="#section-id">Jump to section</a>

<!-- Email link -->
<a href="mailto:you@email.com">Email Me</a>
```

> **Exam tip:** Always use `rel="noopener noreferrer"` with `target="_blank"` for security reasons:
> ```html
> <a href="https://example.com" target="_blank" rel="noopener noreferrer">Link</a>
> ```

---

## Images

```html
<img src="image.jpg" alt="Description of image" width="300" height="200" />
```

| Attribute | Purpose |
|---|---|
| `src` | Path or URL of the image |
| `alt` | Alternative text shown if image fails to load; required for accessibility |
| `width` / `height` | Dimensions — prefer setting in CSS for responsiveness |

> **Exam tip:** The `alt` attribute is not optional — it is required for accessibility and SEO. A missing `alt` is an accessibility violation.

> `<img>` is a void element — it has no closing tag.

---

## Lists

### Unordered List

```html
<ul>
  <li>HTML</li>
  <li>CSS</li>
  <li>JavaScript</li>
</ul>
```

Renders with bullet points. Use when order does not matter.

### Ordered List

```html
<ol>
  <li>Step one</li>
  <li>Step two</li>
  <li>Step three</li>
</ol>
```

Renders with numbers. Use when order matters.

### Nested List

```html
<ul>
  <li>Frontend
    <ul>
      <li>HTML</li>
      <li>CSS</li>
    </ul>
  </li>
  <li>Backend</li>
</ul>
```

> **Exam tip:** Only `<li>` elements should be direct children of `<ul>` or `<ol>`. Placing other tags directly inside a list is invalid HTML.

---

## Key Attributes Covered

| Attribute | Used on | Purpose |
|---|---|---|
| `lang` | `<html>` | Language of the document |
| `charset` | `<meta>` | Character encoding |
| `name`, `content` | `<meta>` | Metadata like viewport, description |
| `href` | `<a>` | Link destination |
| `target` | `<a>` | Where to open the link |
| `rel` | `<a>` | Relationship to linked document |
| `src` | `<img>` | Image source path |
| `alt` | `<img>` | Alternative text |
| `width`, `height` | `<img>` | Image dimensions |
| `title` | any element | Tooltip on hover |

---

## Files in This Folder

| File | Description |
|---|---|
| `index.html` | Main practice page covering all topics above |
| `about.html` | About Me page — practical application of learned tags |
| `education.html` | Education page — used as example of link to local page|

---

## Common Viva / Exam Questions

**Q. What is the difference between `<strong>` and `<b>`?**  
A. `<strong>` is semantic — it indicates the text is of strong importance. `<b>` is purely presentational — it makes text bold with no meaning attached. Screen readers treat them differently.

**Q. Why is `alt` attribute important in `<img>`?**  
A. It provides a text description of the image for screen readers (accessibility), is displayed when the image fails to load, and helps search engines index the image (SEO).

**Q. What does `<!DOCTYPE html>` do?**  
A. It is a document type declaration that tells the browser to render the page using HTML5 standards. Without it, browsers may enter quirks mode and render the page inconsistently.

**Q. What is the difference between `<br>` and `<p>`?**  
A. `<br>` breaks to the next line within the same block. `<p>` creates a new separate paragraph with spacing above and below. Use `<p>` for actual paragraph content, not multiple `<br>` tags.

**Q. What is a void element?**  
A. A void element is an HTML element that has no content and no closing tag. Examples: `<br>`, `<hr>`, `<img>`, `<meta>`, `<link>`, `<input>`.

---

*Part of ITUE203 — Web Development Frameworks*  
*Topic: HTML → 01 HTML Basics*
