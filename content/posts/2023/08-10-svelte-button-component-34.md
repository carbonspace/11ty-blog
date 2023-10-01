---
title: Svelte Button Component
description: Description for Svelte Button Component
date: 2023-08-10
tags:
  - svelte
  - components
  - css
---
The button component communicates actions that a user can take and are typically placed in dialogs, forms, cards and toolbars.

**Buttons are fundamental components that allow users to trigger a defined action.** They can be aligned left, right, or center as the parent container scales and also styled independently or left unstyled to inherit ui styles from any project.

**Button Component Demo**  
[![Open in StackBlitz](https://developer.stackblitz.com/img/open_in_stackblitz.svg)](https://stackblitz.com/edit/vitejs-vite-zewxwp?file=src%2FApp.svelte)

## Button.svelte

In this example, we'll create button component with a few props...

`variant`, which will be the type of button we want

`disabled`, which will be a boolean toggle to disable the button, and

`href`, which will be a link 

Here I've created several variant strings, `back`, `cancel`, `finish`, `logout`, etc., to demonstrate how we can use one button component to handle multiple button styles.

`on:click` is declarative event forwarding.   

> if the on: directive is used without a value, the event will be forwarded, meaning that a consumer can listen for it.  
[Svelte.dev: Component directives](https://svelte.dev/docs/component-directives)

``` js
<script lang="ts">
  export let variant: "back" | "cancel" | "finish" | "logout" | 
    "next" | "submit" = "next";
  export let disabled: boolean = false;
  export let href: string = "";
</script>

<button
  on:click
  {disabled}
  class="button has-text-light is-large is-rounded is-size-3"
  class:is-primary={variant === "submit"}
  class:is-submit={variant === "submit"}
  class:is-cancel={variant === "cancel"}
  class:is-finish={variant === "finish"}
  class:is-next={variant === "next"}
  class:is-back={variant === "back"}
  class:is-logout={variant === "logout"}
>
  { #if href}
    <a class="has-text-light" {href}>
      <slot />
    </a>
  {:else}
    <slot />
  {/if}
</button>

<style>
  button.is-cancel,
  button.is-submit {
		width: 40vw;
  }
</style>
```

## +page.svelte

Add the component to your page

```js
import from '$lib/Button.svelte'  

<Button
  href="#"
  variant="primary"
>
  Text
</Button>
```