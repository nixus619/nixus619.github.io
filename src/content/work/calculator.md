---
title: Calculator
publishDate: 2024-07-12 00:00:00
img: /assets/calculator.png
img_alt: Calculator
description: |
    Using JavaScript, CSS, & HTML, build a fully functioning calculator
tags:
  - JavaScript
  - HTML
  - CSS
---

## Background
This was a project to fully flesh out all my learnings of JavaScript, HTML, CSS and build a fully functioning calculator from scratch. The calculator takes in a max of 8 digits and will perform all basic arithmetic (add, subtract, multiply, & divide) as well as some special functions such as plus/minus and percent. There were only a few special requirements and these included:
- Do not use the eval() function as it has been deemed an enormous security risk.
- Only evaluate a single pair of numbers at a time.
- Display a snarky error message if the user tries to divide by 0.

Other than that, I was free to create it however I saw fit.

### Issues that were worked through
- Number entry and arithmetic overflow: The text box at the top of the calculator only supported 8 characters so special care was needed to account numbers that were very large, very small, and/or had decimals in them.
- Decimals in general: floating point calculation can sometimes get a little funky with JavaSript.
- Differentiating between a number being part of the first number or the start of another number.
- Continuing the evaluation to more iterations. For example, pressing 2 + 2 should evaluate to 4 when another operator is then pressed and then it should be allowed to continue to do further calculations.
- After the equal sign is pressed what happens to the current number. For example, when pressing 2 + 2 and then =, the number 4 should appear. However, if a new number is then pressed this should start a brand new evaluation.

### Links

<a href="https://nixus619.github.io/Calculator/"> Live demo </a>

<a href="https://github.com/nixus619/Calculator"> GitHub repo for project </a>

<a href="https://www.theodinproject.com/lessons/foundations-calculator"> Project Prompt </a>