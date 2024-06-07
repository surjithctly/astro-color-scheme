# Astro Color Scheme

Astro Color Scheme is a fully headless dark mode theme toggle for Astro.

[**Live Demo on Stackblitz →**](https://stackblitz.com/edit/github-jpfnv9-ep5z59?file=src%2Fpages%2Findex.astro)

[**Live Demo on Stablo Template →**](https://stablo-astro.web3templates.com/)

## Installation

```
npm install astro-color-scheme
# or
pnpm add astro-color-scheme
```

## Basic Usage

You can toggle the theme using `button`, `select`, `checkbox` or `radio` inside the `<ThemeSwitch>`.

```jsx
---
import { ThemeSwitch } from "astro-color-scheme";
---

<div>
  <ThemeSwitch strategy="button">
    <button>Toggle Theme</button>
  </ThemeSwitch>
</div>
```

<details>
<summary>Advanced Examples</summary>

**Using Select:**

```jsx
---
import { ThemeSwitch } from "astro-color-scheme";
---

<div>
  <ThemeSwitch strategy="select" defaultTheme="system">
    <select>
      <option value="system">System</option>
      <option value="dark">Dark</option>
      <option value="light">Light</option>
    </select>
  </ThemeSwitch>
</div>
```

**Using Radio:**

```jsx
---
import { ThemeSwitch } from "astro-color-scheme";
---

<div>
  <ThemeSwitch strategy="radio" defaultTheme="system" as="div">
    <form>
      <label><input type="radio" name="theme" value="system" />System</label>
      <label><input type="radio" name="theme" value="dark" />Dark</label>
      <label><input type="radio" name="theme" value="light" />Light</label>
    </form>
  </ThemeSwitch>
</div>
```

</details>

<details>
<summary>Set theme without any toggle</summary>

```jsx
---
import { ThemeSwitch } from "astro-color-scheme";
---

<div>
  <ThemeSwitch defaultTheme="dark"/>
</div>
```

</details>

## Options

Options for `ThemeSwitch`

| option         | required                     | notes                                                           |
| -------------- | ---------------------------- | --------------------------------------------------------------- |
| `strategy`     | `required` if you use toggle | Possible values: `button`, `checkbox`, `select` or `radio`      |
| `defaultTheme` | `optional`                   | Default: `system`, Possible values: `light`, `dark` or `system` |
| `as`           | `optional`                   | Default: `span`, Possible values: `div`, `span`                 |

The `as` option lets you select what wrapper element to use for the ThemeSwitch. Elements Allowed for Toggle inside `ThemeSwitch` are `<button>`, `<input type=checkbox>`, `<select>`, `<form>`.

```html
<!-- Button -->
<button>Toggle Theme</button>

<!-- Checkbox -->
<input type="checkbox" />

<!-- Select -->
<select>
  <option value="system">System</option>
  <option value="dark">Dark</option>
  <option value="light">Light</option>
</select>
```

## Customizations

As a headless plugin, You are free to add your own styles and icons based on the theme.

Here's an example on how to add custom styles using css variables.

```html
<style>
  html {
    --background-color: white;
    --text-color: black;
    color: var(--text-color);
    background-color: var(--background-color);
  }
  .dark {
    --background-color: black;
    --text-color: white;
  }
  /* OR */
  [data-theme="dark"] {
    --background-color: black;
    --text-color: white;
  }
</style>
```

Here's an example shows usage of Astro Icon.

```jsx
---
import { Icon } from "astro-icon";
import { ThemeSwitch } from "astro-color-scheme";
---

<div>
  <ThemeSwitch strategy="button">
    <button>
      <span class="sr-only">Toggle Theme</span>
      <Icon class="dark:hidden" name="heroicons-outline:sun" />
      <Icon class="hidden dark:block" name="heroicons-outline:moon" />
    </button>
  </ThemeSwitch>
</div>
```

This plugin also supports custom checkbox switch with animations. Just use `strategy="checkbox"` and add your content. By default we add `dark/light` class into the `html` as well as `data-theme` attribute. Here's how it would look like:

```html
<html lang="en" class="dark" data-theme="dark"></html>
```

## Tailwind CSS

This plugin should work well with regular CSS as well as Tailwind CSS. You can style the `dark` mode using `dark:` modifier to add custom icon based on the chosen theme. Make sure you change the `darkMode` to `class` to make this work.

```js
// tailwind.config.cjs
 darkMode: "class",
```

</details>

## Contribute

Please create an issue.

## Credits

Copyright ©️ 2023-2099. [Surjith S M](https://twitter.com/surjithctly).
