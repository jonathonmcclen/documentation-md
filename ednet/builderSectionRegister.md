Absolutely! Here's a more polished and professionally formatted version of your documentation, with improved grammar, clarity, and structure:

---

# Section Type & Builder Documentation

## Overview

A **section** is defined as a Next.js component within the `ednet` GitHub repository. Each component must follow a specific set of conventions in order to be compatible with the Ednet CMS powered by Sanity Studio.

---

## Component Requirements

### Naming Convention

- Each component **must have a unique name**.
- No two components can share the same functional or class component name.

### Props Structure

All section components accept the following props:

- `obj`: An object containing the content for the section.
- `colors`: An array of theme colors, typically `[theme.primary, theme.secondary, ...]`.

#### `obj` Usage

- Keys in `obj` represent content fields and must match exactly (case-sensitive) with the `definitions` registered in AWS.
- Example key usage in JSX:
  ```jsx
  obj.header, obj.title, obj.href, obj.imgAlt;
  ```

#### `colors` Usage

- Use the `colors` array to dynamically style your section using inline styles:
  ```jsx
  <div style={{ backgroundColor: colors[0] }}>
  ```

#### Accessibility

- **All images must include an `alt` tag** for accessibility.
- If using `obj.imgSrc`, ensure that `obj.imgAlt` is also provided.

---

## Example: `MediaRightSection`

```jsx
"use client";

import { ArrowRightIcon } from "@heroicons/react/24/solid";
import Image from "next/image";

export default function MediaRightSection({ obj, colors }) {
  return (
    <section className="py-16 px-4 sm:px-6 lg:px-8">
      <div className="max-w-7xl mx-auto grid grid-cols-1 md:grid-cols-2 gap-12 items-center">
        {/* Right Media - appears first on mobile, right on desktop */}
        <div className="relative w-full h-64 sm:h-80 lg:h-96 order-1 md:order-2">
          <Image
            src={obj?.src}
            alt={obj?.alt}
            fill
            className="rounded-xl object-cover shadow-lg"
            priority
          />
        </div>

        {/* Left Text Content */}
        <div className="order-2 md:order-1">
          <h2 className="text-3xl font-bold tracking-tight text-gray-900 dark:text-white sm:text-4xl">
            {obj?.title}
          </h2>
          <p className="mt-4 text-lg text-gray-600 dark:text-gray-300">
            {obj?.content ||
              "Discover the power of our platform, designed to accelerate your growth and drive success."}
          </p>

          {obj?.btnLink && (
            <div className="mt-6">
              <a
                href={obj?.btnLink}
                className="inline-flex items-center gap-2 px-6 py-3 bg-blue-600 text-white text-sm font-medium rounded-lg shadow hover:bg-blue-700 transition"
              >
                {obj?.btnTxt || "Get Started"}
                <ArrowRightIcon className="h-5 w-5" />
              </a>
            </div>
          )}
        </div>
      </div>
    </section>
  );
}
```

---

## Importing Into Ednet 2.0

Once your component is created, import it into the platform by editing:

```
/components/builder/import.js
```

- If exported as `default`, you can import it using an alias.
- The alias you assign becomes the **component name**, which must match the registration name in AWS (case-sensitive).

---

## Registering a Component in AWS

### DynamoDB Table

Use the table named:

```
section_types (v1)
```

Each entry must include:

- **`component`**: The name used in the `import.js` file (case-sensitive).
- **`section`**: An object with the following structure:

```json
{
  "type": "hero_8",
  "component": "hero_8",
  "definitions": {
    "title": "STRING",
    "paragraph": "STRING",
    "btnTxt": "STRING",
    "secondaryLinkTxt": "STRING",
    "img1src": "STRING",
    "img2src": "STRING",
    "img3src": "STRING",
    "img4src": "STRING",
    "img5src": "STRING"
  }
}
```

> 🔹 **Note**: `type` and `component` are included in preparation for v2 and should match the `component` field for now.

### Definitions

- `definitions` must reflect the keys used in your Next.js component’s `obj` prop.
- All values should currently be `"STRING"`.
- Future support will include other types like `textArea`, `colorPicker`, `file`, `image`, `richText`, etc.

---

## Final Steps

Once your section is:

- Committed to the GitHub repo
- Imported in `import.js`
- Registered in DynamoDB

And you've redeployed Ednet 2.0...

✅ Your new section will appear in the Ednet CMS (powered by Sanity Studio) and will be fully customizable!

---

Let me know if you'd like this turned into a downloadable Markdown file or integrated into your existing documentation site.
