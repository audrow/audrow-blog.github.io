---
title: Visualizing my cash flow with Observable and D3js
tags:
  - money
  - visualization
  - d3js
  - observable
categories:
  - webdev
comments: true
excerpt: |
  <iframe width="100%" height="514" frameborder="0" src="https://observablehq.com/embed/@audrow/visualizing-cash-flow-demo?cell=treeMap"></iframe>
date: 2021-01-07 21:44:44
---


![](visualizing-cash-flow-banner.jpg "Money banner")

I think that it's important to understand where your money is going.
I find this hard to do with most of the tools I've tried.
The online services I have tried (at least five different ones, including Mint and Personal Capital) often do pretty lame clustering of my spending (no Mint, my paycheck is not auto insurance) and savings.
My spending is pretty regular, so I'm more interested to get a big picture understanding of where my money is going, so that I can see if I'm being particularly wasteful in any areas.
It also helps to have a sense of scale between areas of my spending.

Previously I have used spreadsheets or just white paper to sum up everything.
This works, but it isn't very general: I have to redo it every time I want to reexamine my cash flow.
It is also difficult to see how nesting works with expense categories.
For example, I want to see how much I'm spending on 'food' but it'd also be nice to see exactly what I'm eating and its relative cost. As a lazy programmer, I felt like I could do better (less).

What I've made is a page on Observable that uses D3 to make a zoomable tree map to help me understand my data.
The program normalizes all of savings and expenses to the same unit time (in this case, one month) so that it can be compared.
You show nesting in the structure by having nested objects, to an arbitrary level.
Give it a try!

<iframe width="100%" height="514" frameborder="0"
  src="https://observablehq.com/embed/@audrow/visualizing-cash-flow-demo?cell=treeMap"></iframe>

You can find the full project [here](https://observablehq.com/@audrow/visualizing-cash-flow-demo) and it includes instructions for using it for yourself.

Some things that I have considered adding to this project are as follows:
* Ability to merge expenses in the same category but different time period together
* A toggle to change the amount of time considered (e.g., daily, monthly, yearly, etc.)
* Showing your idealized savings in addition to your actual savings

Is this useful?
If you tried it, did anything about your cash flow surprise you?