Here’s the **Markdown documentation** for your updated `NavFooter1` component. This is tailored for **marketers and content editors using Sanity**, focusing on how to input and structure footer data correctly:

---

# 📄 `NavFooter1` – Footer Component Documentation

The `NavFooter1` component is a structured and flexible **footer** section designed to pull its content from **Sanity CMS** through a JSON string called `navigation`. It displays branding, multiple navigation columns, and social links.

---

## 🧑‍💼 Who Is This For?

This guide is for **marketers or content managers** using **Sanity Studio** to update the footer content on a website built using this component.

---

## 🔧 Component Usage

```tsx
<NavFooter1 obj={sanityFooterObject} colors={{}} />
```

- `obj`: Sanity document object. This **must include** a stringified JSON field named `navigation`.
- `colors`: Optional color overrides (currently unused but reserved for future theming).

---

## 🔑 Required Field in Sanity

You will configure a **single field** in your Sanity schema:

### `navigation` (type: `text` or `string`)

This field should contain a **JSON string** that defines all footer sections. It must include:

- Navigation column groups
- Social links
- Logo URL

---

## 🧱 JSON Structure Example

Here’s a fully working example you can paste into the Sanity `navigation` field:

```json
[
  {
    "title": "Solutions",
    "type": "List",
    "listItems": [
      { "title": "Marketing", "href": "#" },
      { "title": "Analytics", "href": "#" },
      { "title": "Automation", "href": "#" },
      { "title": "Commerce", "href": "#" },
      { "title": "Insights", "href": "#" }
    ]
  },
  {
    "title": "Support",
    "type": "List",
    "listItems": [
      { "title": "Submit ticket", "href": "#" },
      { "title": "Documentation", "href": "#" },
      { "title": "Guides", "href": "#" }
    ]
  },
  {
    "title": "Company",
    "type": "List",
    "listItems": [
      { "title": "About", "href": "#" },
      { "title": "Blog", "href": "#" },
      { "title": "Jobs", "href": "#" },
      { "title": "Press", "href": "#" }
    ]
  },
  {
    "title": "Legal",
    "type": "List",
    "listItems": [
      { "title": "Terms of service", "href": "#" },
      { "title": "Privacy policy", "href": "#" },
      { "title": "License", "href": "#" }
    ]
  },
  {
    "type": "Socials",
    "listItems": [
      { "title": "Facebook", "href": "#", "icon": "facebook" },
      { "title": "Instagram", "href": "#", "icon": "instagram" },
      { "title": "X", "href": "#", "icon": "x" },
      { "title": "GitHub", "href": "#", "icon": "github" },
      { "title": "YouTube", "href": "#", "icon": "youtube" }
    ]
  },
  {
    "type": "Logo",
    "src": "https://tailwindcss.com/plus-assets/img/logos/mark.svg?color=indigo&shade=600"
  }
]
```

---

## 🧭 Key Sections Explained

### 1. 🧩 `type: "List"` – Navigation Columns

Each object with `type: "List"` appears as a column in the footer with a title and list of links.

```json
{
  "title": "Company",
  "type": "List",
  "listItems": [
    { "title": "About", "href": "/about" },
    { "title": "Blog", "href": "/blog" }
  ]
}
```

---

### 2. 🌐 `type: "Socials"` – Social Media Links

This displays clickable icons for each social media platform. You must include an `icon` name matching your icon system (`icon-facebook`, `icon-x`, etc.).

```json
{
  "type": "Socials",
  "listItems": [{ "title": "X", "href": "#", "icon": "x" }]
}
```

---

### 3. 🖼️ `type: "Logo"` – Logo Image

This displays the logo at the top of the footer. Provide a direct image URL:

```json
{
  "type": "Logo",
  "src": "https://example.com/logo.svg"
}
```

---

## 🔒 Best Practices for Editors

- ✅ Use a [JSON formatter](https://jsonlint.com) before pasting into Sanity.
- ✅ Keep `title` and `href` accurate and up to date.
- ✅ Ensure the `navigation` field is **a string**, not a rich object.
- ⚠️ All `href` values must be valid URLs or internal paths (e.g., `/blog`, `https://example.com/about`).
- 🚫 Avoid trailing commas in JSON to prevent breaking the layout.

---

## 🛠 Developer Notes

- The component expects `obj.navigation` to be a **valid JSON string**.
- A `defaultNavigation` fallback exists for local previewing.
- Social icons render via class names like `icon-facebook`, `icon-instagram`, etc. You can replace these with actual icon components if desired.

---

Let me know if you’d like a downloadable `.md` version or to embed this guide directly into your Sanity schema descriptions.
