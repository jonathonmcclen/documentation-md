# Micro-Credential Categories

The **Micro-Credential Categories** feature in the EdNet 2.0 platform allows a single micro-credential to appear in multiple categories and subcategories. Categories are handled **recursively**, supporting an **infinite number of child categories**.

---

## Example

A micro-credential like _Cyber Security Certification_ can appear under:

1. **Computer Science**
2. **Micro-Credentials > Computer Science > Security**

---

## Schema: Products

All category data is stored in the **Products** schema.

### Table: `categories`

The `categories` table manages the category hierarchy. In the **admin portal**, you'll find a column named `parent_category`. Categories with no value in `parent_category` are the **top-level categories**.

### Setting Parent Categories

To assign a parent category, add the **ID** of another category to the `parent_category` column.

For example:

| ID  | Name             | Parent_Category |
| --- | ---------------- | --------------- |
| 1   | Computer Science | NULL            |
| 2   | Security         | 1               |

Here, the **Security** category has **Computer Science** as its parent.

---

## Front-End Handling

When a category ID is received on the front end, the application:

1. Checks the `parent_category` column.
2. Collects all parent categories recursively.
3. Displays the collected hierarchy in the **breadcrumbs** for easy navigation.

once there are no more categoris we then will map thorugh the microcredentials or degree programs table.
