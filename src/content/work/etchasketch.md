---
title: Etch-a-Sketch
publishDate: 2024-07-03 00:00:00
img: /assets/etchasketch.png
img_alt: etch-a-sketch
description: |
    Create your own etch-a-sketch using Javascript
tags:
  - JavaScript
  - HTML
  - CSS
---

## Background
Here is a project in manipulating the DOM as there is almost no HTML/CSS included. For this project, the page loads a simple 16x16 grid. As you move your cursor over the boxes, they will fill with a random color and opacity. If you were to return to that same square, the opacity would go up by 10% until it is a completely colored square. There is also buttons at the top which will let you resize the grid and reset it, while maintaining the same total space of the original container.

It was initially tough to create a grid of the exact size I wanted, especially through javascript only. Eventually I settled on creating the columns first and then creating the rows all while using Flexbox to make it a perfect box of n size, every time. The next hurdle to get through was to ensure that when mousing over a square that already had a color to not select a new random color and instead make the color increase in opacity, so I needed to mess around with the specific cells style. Finally, on reset and resize, everything needed to be reset to their initial color/opacity so when the user begins to fill the box in again, the existing functions continue to work. 

<a href="https://nixus619.github.io/etch-a-sketch/"> Live demo </a>

<a href="https://github.com/nixus619/etch-a-sketch"> GitHub repo for project </a>

<a href="https://www.theodinproject.com/lessons/foundations-etch-a-sketch"> Project Prompt </a>