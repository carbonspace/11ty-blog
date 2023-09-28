---
title: Testing Svelte Apps
description: Post description about Testing Svelte Apps.
date: 2023-09-07
tags:
  - svelte
  - testing
---

A Svelte application will typically have three different types of tests: `Unit`, `Component`, and `End-to-End (E2E)`.

**Unit Tests**: Focus on testing business logic in isolation. Often this is validating individual functions and edge cases. By minimizing the surface area of these tests they can be kept lean and fast, and by extracting as much logic as possible from your Svelte components more of your application can be covered using them. When creating a new SvelteKit project, you will be asked whether you would like to setup [Vitest][vitest] for unit testing. There are a number of other test runners that could be used as well.

**Component Tests**: Validating that a Svelte component mounts and interacts as expected throughout its lifecycle requires a tool that provides a Document Object Model (DOM). Components can be compiled (since Svelte is a compiler and not a normal library) and mounted to allow asserting against element structure, listeners, state, and all the other capabilities provided by a Svelte component. Tools for component testing range from an in-memory implementation like jsdom paired with a test runner like [Vitest][vitest] to solutions that leverage an actual browser to provide a visual testing capability such as [Playwright][playwright] or [Cypress][cypress].

**End-to-End Tests**: To ensure your users are able to interact with your application it is necessary to test it as a whole in a manner as close to production as possible. This is done by writing end-to-end (E2E) tests which load and interact with a deployed version of your application in order to simulate how the user will interact with your application. When creating a new SvelteKit project, you will be asked whether you would like to setup [Playwright][playwright] for end-to-end testing. There are many other E2E test libraries available for use as well.


Some resources for getting started with testing:


- [Svelte Testing Library][svelte-testing-library]
- [Svelte Component Testing in Cypress][svelte-component-testing]
- [Example using vitest][testing-with-vitest]
- [Example using uvu test runner with JSDOM][testing-with-uvu-and-jsdom]
- [Test Svelte components using Vitest & Playwright][testing-with-vitest-and-playwright]
- [Component testing with WebdriverIO][component-testing-with-webdriverio]

<br>

Source: [How to Test Svelte Apps][source]

[//]: # (Reference Links)

[vitest]: <https://vitest.dev/>
[playwright]: <https://playwright.dev/docs/test-components>
[cypress]: <https://www.cypress.io/>
[svelte-testing-library]: <https://testing-library.com/docs/svelte-testing-library/example/>
[svelte-component-testing]: <https://docs.cypress.io/guides/component-testing/svelte/overview>
[testing-with-vitest]: <https://github.com/vitest-dev/vitest/tree/main/examples/svelte>
[testing-with-uvu-and-jsdom]: <https://github.com/lukeed/uvu/tree/master/examples/svelte>
[testing-with-vitest-and-playwright]: <https://davipon.hashnode.dev/test-svelte-component-using-vitest-playwright>
[component-testing-with-webdriverio]: <https://webdriver.io/docs/component-testing/svelte>

[source]: <https://svelte.dev/docs/faq#how-do-i-test-svelte-apps>
