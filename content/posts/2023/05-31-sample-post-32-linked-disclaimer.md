---
title: Debugging in VS Code
description: Debugging in VS Code
date: 2023-05-31
tags:
  - vscode
  - debugging
  - debug configuration
disclaimer:
  text: VS Code Debugging documentation
  url: https://code.visualstudio.com/docs/editor/debugging
---

One of the key features of Visual Studio Code is its great debugging support. VS Code's built-in debugger helps accelerate your edit, compile, and debug loop.


## Debugging Tools

Visual Studio Code comes with a built-in debugger that provides a rich set of features for debugging your code. Here are some of the most useful debugging tools in VS Code:

**Breakpoints:** You can set breakpoints in your code where you want the execution to pause. This allows you to inspect the current state of your program. You can set conditional breakpoints, logpoints, and function breakpoints.

**Variable Inspection:** When your code execution is paused, you can hover over variables to see their current values. You can also see a list of all local and global variables in the debug sidebar.

**Step Through Code:** You can step through your code line by line to see how it executes. You can step over functions, step into functions, or step out of functions.

**Call Stack Inspection:** You can inspect the call stack to see which functions were called to get to the current point in your code.

**Watch Expressions:** You can create watch expressions that allow you to keep an eye on specific variables and expressions over time.

**Debug Console:** The debug console lets you interact with your program while it's being debugged. You can evaluate expressions, inspect variables, and more.

**Multi-target Debugging:** VS Code allows you to debug multiple targets at once. This is useful if you're working on a full-stack application and need to debug both the client and server side of your application.

**Debugging Configurations:** You can create and save debugging configurations for different tasks in your project. This makes it easy to start debugging with the right settings.


## Debug Code in VSCode

Debugging your code in Visual Studio Code involves several steps:

**Set up a Debug Configuration:** VS Code uses a file called `launch.json` to configure the debugger for your project. This file is located in a `.vscode` folder at the root of your project. If this file doesn't exist, you can create it by going to the `Run view (Ctrl + Shift + D)`, and clicking on `create a launch.json file`. For a Node.js project, you might select `Node.js` as the environment.

**Set Breakpoints:** Click in the gutter to the left of the line numbers in your code to set a breakpoint. The debugger will pause execution at these points.

**Start Debugging:** You can start debugging by going to the Run view and clicking on Start Debugging, or by pressing F5. The debugger will start your program and pause at the first breakpoint.

**Inspect Variables:** When the debugger is paused, you can hover over variables in your code to see their current values. You can also see a list of all local and global variables in the debug sidebar.

**Step Through Code:** Use the debug controls at the top of the screen to `step over lines (F10)`, `step into functions (F11)`, or `step out of functions (Shift + F11)`. This allows you to control the execution of your code line by line.

**Modify Variables:** In the debug sidebar, you can modify the values of variables by `clicking on the pencil icon` next to the variable's value.

**Continue Execution:** `Click on the Continue button (F5)` in the debug controls to continue execution until the next breakpoint.


## Using the Debug Console in VSCode

The Debug Console in Visual Studio Code allows you to interact with your program while it's being debugged. Here's how you can use it:

**Open the Debug Console:** You can open the Debug Console by `clicking on View > Debug Console` in the menu, or by using the shortcut `Ctrl + Shift + Y`.

**Start Debugging:** Start your debugging session by `pressing F5` or by `clicking on Start Debugging` in the `Run` view. Your program will run and any output will be displayed in the Debug Console.

**Interact with Your Program:** You can type commands into the input box at the bottom of the Debug Console. These commands will be evaluated in the context of your debugging session. For example, you can evaluate expressions, inspect variables, call functions, etc.

**View Output:** Any output from your program, such as console.log statements in JavaScript, will be displayed in the Debug Console. Error messages and stack traces will also be displayed here.

**Navigate Through Previous Commands:** You can use the up and down arrow keys in the input box to navigate through your previously entered commands.

Remember, the Debug Console is only active when you're in a debugging session. If you're not currently debugging, the input box at the bottom of the Debug Console will be disabled.


## Using Watch Expressions in VSCode

Watch expressions in Visual Studio Code allow you to keep an eye on specific variables and expressions over time. Here's how you can use them:

**Start Debugging:** Start your debugging session by `pressing F5` or by `clicking on Start Debugging` in the `Run` view.

**Open the Watch View:** `Click on the watch icon` in the `Run` view to open the Watch view.

**Add a Watch Expression:** `Click on the + button` at the top of the `Watch` view to add a new watch expression. Enter the expression you want to watch in the input box that appears. This could be a variable name, a complex expression, or a function call.

**Inspect the Watch Expression:** Once you've added a watch expression, its current value will be displayed next to it in the Watch view. This value will be updated as you step through your code.

**Modify a Watch Expression:** You can modify a watch expression by clicking on it in the Watch view. This will open an input box where you can change the expression.

**Remove a Watch Expression:** You can remove a watch expression by clicking on the x button next to it in the Watch view.

Remember, watch expressions are evaluated in the context of your debugging session, so they have access to all local and global variables. If a watch expression can't be evaluated, it will display an error message.


## Modify the Launch Configuration for a Debugging Session in VSCode

Modifying the launch configuration for your debugging session in Visual Studio Code involves editing the `launch.json` file. Here's how you can do it:

**Open the Debug View:** `Click on the bug icon` in the `Activity Bar` on the side of VS Code to open the Debug view.

**Open launch.json:** Click on the gear icon at the top of the Debug view to open your `launch.json` file. If this file doesn't exist, VS Code will create a new one for you with some default configurations.

**Edit the Configuration:** In the `launch.json` file, you'll see a list of configurations. Each configuration is a separate way to start a debugging session. You can modify the properties of these configurations to suit your needs. For example, you might change the program property to point to a different file, or add new properties like env to set environment variables.

Here's an example of what a configuration for a Node.js application might look like:

``` sh
{
  "version": "0.2.0",
  "configurations": [
    {
      "type": "node",
      "request": "launch",
      "name": "Launch Program",
      "program": "${workspaceFolder}/app.js",
      "env": {
        "NODE_ENV": "development"
      }
    }
  ]
}
```

Save the File: After you've made your changes, save the launch.json file. Your new configurations will be available in the Debug view.

Remember, the exact properties you'll need in your `launch.json` file will depend on the type of application you're debugging. You can find more information about these properties in the VS Code Debugging documentation [https://code.visualstudio.com/docs/editor/debugging].