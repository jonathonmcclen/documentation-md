Here is the markdown documentation tailored for marketers using **Sanity** to populate navigation content through the `NavHeader1` component:

---

# 🧭 `NavHeader1` - Navigation Header Component

The `NavHeader1` component renders a responsive navigation header that is powered by **Sanity content**, particularly focused on the `obj` prop. It includes support for logo, login link, CTA button, and complex menu structures with dropdowns and submenus.

## 💼 Who Should Use This?

**Marketers and content managers** using **Sanity Studio** to manage navigation content for university or institutional websites.

---

## 🧩 Component Overview

```jsx
<NavHeader1 obj={sanityNavigationObject} colors={{}} />
```

- `obj`: This is the main prop you will configure in **Sanity**. It controls the logo, CTA buttons, login links, and navigation menu.
- `colors`: Currently unused, but prepared for future theme support.

---

## 🧷 Required Fields in `obj`

Your Sanity document must include these fields. Here's a breakdown:

| Field        | Type                             | Description                                                                  |
| ------------ | -------------------------------- | ---------------------------------------------------------------------------- |
| `logo`       | `string (URL)`                   | Image URL of the logo. Displayed at the top-left.                            |
| `logoAlt`    | `string`                         | Alt text for the logo image.                                                 |
| `login`      | `string` (`"true"` or `"false"`) | Whether to show a "Log In" link.                                             |
| `loginHref`  | `string (URL)`                   | The URL the logo (and optionally login) should link to.                      |
| `ctaBtn`     | `string`                         | Text for the call-to-action button (e.g., "Apply Now").                      |
| `ctaBtnHref` | `string (URL)`                   | URL that the CTA button navigates to.                                        |
| `menueItems` | `JSON stringified array`         | Menu items including optional submenus. **Must be a JSON string** in Sanity! |

> ✅ **Important**: `menueItems` must be entered in **valid JSON format**. Do not forget to wrap the array in quotes in the CMS, as Sanity treats this as a string field.

---

## 🧭 `menueItems` Format

Here’s an example of a correctly formatted `menueItems` JSON string for Sanity:

```json
[
  { "title": "Home", "href": "/" },
  { "title": "FAQ", "href": "/faq" },
  { "title": "Articles", "href": "/articles" },
  {
    "title": "Programs",
    "href": "#",
    "subMenu": [
      { "title": "Undergraduate Programs", "href": "/programs/undergraduate" },
      { "title": "Graduate Programs", "href": "/programs/graduate" },
      { "title": "PhD Programs", "href": "/programs/phd" },
      { "title": "Online Programs", "href": "/programs/online" },
      { "title": "Professional Development", "href": "/programs/professional" }
    ]
  }
]
```

You can define:

- A simple menu item (with just `title` and `href`), or
- A complex menu item with a `subMenu` array (each having its own `title` and `href`).

---

## 📱 Responsive Behavior

- On **desktop**: Dropdown menus appear when hovering/clicking top-level items.
- On **mobile**: The menu collapses into a hamburger and expands with **accordion-style Disclosure components**.

---

## ✅ Example Sanity Setup

In your Sanity Studio, define a document schema (e.g., `navigationHeader`) and use string fields for:

- `logo`
- `logoAlt`
- `login`
- `loginHref`
- `ctaBtn`
- `ctaBtnHref`
- `menueItems` (stored as a **JSON string**)

---

## 🧪 Tips for Marketers

- Use a **JSON validator** like [https://jsonlint.com](https://jsonlint.com) to ensure your `menueItems` are correctly formatted.
- Double-check `href` fields to ensure they point to correct routes.
- Use `"true"` as a string (not a boolean) for the `login` field to display the login button.
- For accessibility, keep `logoAlt` descriptive (e.g., "University Logo").

---

## 🛠️ Developer Notes

- The component uses **Headless UI** (`Popover`, `Dialog`, `Disclosure`) and **Heroicons** for interactivity and icons.
- `useEffect` dynamically parses `obj.menueItems` if provided as a JSON string.
- The component is fully client-rendered using `"use client"` directive for Next.js 13+ App Router compatibility.

---
