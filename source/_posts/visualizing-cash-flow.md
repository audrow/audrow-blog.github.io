---
title: Visualizing my cash flow with Observable and D3js
tags:
  - Demo
categories:
  - [Programming, Javascript, D3js]
  - [Programming, Platforms, Observable]
  - [Domain, Visualization]
comments: true
excerpt: |
  <br>
  It is hard to prioritize when you don't have the full picture.
  One area where this is true for me has been my cash flow.
date: 2021-01-07 21:44:44
---

<iframe width="100%" height="440" frameborder="0" 
  src="https://observablehq.com/embed/@audrow/visualizing-cash-flow-demo?cell=treeMap"></iframe>

It is hard to prioritize when you don't have the full picture.
One area where this is true for me has been my cash flow.
The online services I have tried (like Mint and Personal Capital) do a pretty lame job of clustering my spending (no Mint, my paycheck is not auto insurance) and savings.
Also, my cash flow doesn't vary much from month-to-month, so I decided to make a [small tool on Observable](https://observablehq.com/@audrow/visualizing-cash-flow-demo) to help me see where my money is going.
Donald Knuth said that "Premature optimization is the root of all evil," and this way, I can better see where I should put attention to reduce my spending or increase my savings.
The tool I made uses [D3js](https://d3js.org/) for visualization and is on [Observable](https://observablehq.com), a kind of Jupyter Notebook for Javascript.
You can see a Pirate-themed demo above - try clicking around.

## How it works

Cashflow is broken down into four categories:

- Taxes
- Expenses
- Savings
- Unallocated (money that you could possibly save 😉)

In the project, you enter your total income, the percentage of that income that you keep after taxes, and then your regular expenses and savings.
(The project is using local specific formatting, so feel free to change the region and currency.)
To support nesting, expenses and savings are represented in [Javascript Object Notation (JSON)](https://www.json.org/json-en.html).
For example,

{% codeblock lang:javascript %}
let savings = {
  treasureChest: {
    gold: 200,
    silver: 100,
  },
  retirement: {
    rothIra: 500,
  }
}
{% endcodeblock %}

In this case, the total savings is 800, with 300 in the treasure chest and 500 in retirement accounts.
If you look into the `treasureChest` you then see that 200 is in gold and 100 in silver.

Actually, the current format combines entries that are made in different time spans, so you can enter things like:

{% codeblock lang:javascript %}
let weeklySavings = {
  treasureChest: {
    gold: 60,
    silver: 30,
  },
};
let monthlySavings = {
  retirement: {
    rothIra: 500,
  },
};
{% endcodeblock %}

and they will be combined for the same amount of time (currently, monthly).

As you make these changes, they will immediately be reflected in the Observable project.
Happy visualizing!

## Ending thoughts

You can find the [full project on Observable](https://observablehq.com/@audrow/visualizing-cash-flow-demo) and it includes instructions for using it for yourself.

Some things that I have considered adding to this project are as follows:

- Ability to merge expenses in the same category but different time period together
- A toggle to change the amount of time considered (e.g., daily, monthly, yearly, etc.)
- Showing your idealized savings in addition to your actual savings

Is this useful?
If you tried it, did anything about your cash flow surprise you?
