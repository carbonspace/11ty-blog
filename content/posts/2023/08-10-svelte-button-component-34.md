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

**Buttons are fundamental components that allow users to trigger a defined action.** They can be aligned left, right, or center as the parent container scales.

``` js

<script lang="ts">
  export let variant: "back" | "cancel" | "finish" | "logout" | "next" | "submit" = "next";
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