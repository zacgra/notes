# CSS Rule Specificity

# The four number calculation

The four numbers that the specificity calculation are, in increasing order of importance

the number of tag selectors in the selector
the number of class, pseudo-element, and attribute selectors in the selector
the number of id selectors in the selector
is this an inline style
Hopefully, you don't put inline styles in your HTML. So, you can ignore that last one and focus on the first three.

The algorithm to determine the most specific rule goes like this. When comparing two selectors

If one has a greater number of ids, then it wins. If there is a winner, STOP.
They must have the same number of ids, so the one with the greater number of classes, pseudo-classes, and attributes wins. If there is a winner, STOP.
They must have the same number of ids and the same number of classes, too. The rule with the greatest number of tags wins. If there is a winner, STOP.
They have the same number of ids, classes, and tags. The rule that the browser read last wins.

Here is a variety of CSS selectors and their three-number scores. Assume that this is the order in which the browser read them from various CSS files.

<table>
<thead>
<tr>
<th>Selector</th>
<th style="text-align: center;"># of ids</th>
<th style="text-align: center;"># of classes/attributes</th>
<th style="text-align: center;"># of tags</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>.header</code></td>
<td style="text-align: center;">0</td>
<td style="text-align: center;">1</td>
<td style="text-align: center;">0</td>
</tr>
<tr>
<td><code>.nav .current</code></td>
<td style="text-align: center;">0</td>
<td style="text-align: center;">2</td>
<td style="text-align: center;">0</td>
</tr>
<tr>
<td><code>#main-header</code></td>
<td style="text-align: center;">1</td>
<td style="text-align: center;">0</td>
<td style="text-align: center;">0</td>
</tr>
<tr>
<td><code>#main-header.large.on</code></td>
<td style="text-align: center;">1</td>
<td style="text-align: center;">2</td>
<td style="text-align: center;">0</td>
</tr>
<tr>
<td><code>div.header</code></td>
<td style="text-align: center;">0</td>
<td style="text-align: center;">1</td>
<td style="text-align: center;">1</td>
</tr>
<tr>
<td><code>div#main-header.header</code></td>
<td style="text-align: center;">1</td>
<td style="text-align: center;">1</td>
<td style="text-align: center;">1</td>
</tr>
<tr>
<td><code>div</code></td>
<td style="text-align: center;">0</td>
<td style="text-align: center;">0</td>
<td style="text-align: center;">1</td>
</tr>
<tr>
<td><code>ul &gt; li</code></td>
<td style="text-align: center;">0</td>
<td style="text-align: center;">0</td>
<td style="text-align: center;">2</td>
</tr>
<tr>
<td><code>ul li a.current</code></td>
<td style="text-align: center;">0</td>
<td style="text-align: center;">1</td>
<td style="text-align: center;">3</td>
</tr>
<tr>
<td><code>ul li</code></td>
<td style="text-align: center;">0</td>
<td style="text-align: center;">0</td>
<td style="text-align: center;">2</td>
</tr>
<tr>
<td><code>ul.nav li a.current</code></td>
<td style="text-align: center;">0</td>
<td style="text-align: center;">2</td>
<td style="text-align: center;">3</td>
</tr>
<tr>
<td><code>ul.nav li a</code></td>
<td style="text-align: center;">0</td>
<td style="text-align: center;">1</td>
<td style="text-align: center;">3</td>
</tr>
</tbody>
</table>

From that table, here are some comparisons to see which would win.

<table>
<thead>
<tr>
<th>Selector 1</th>
<th style="text-align: center;">Score</th>
<th style="text-align: center;">Winner</th>
<th style="text-align: center;">Score</th>
<th>Selector 2</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>.nav .current</code></td>
<td style="text-align: center;">0-2-0</td>
<td style="text-align: center;">&lt;-</td>
<td style="text-align: center;">0-0-1</td>
<td><code>div</code></td>
</tr>
<tr>
<td><code>.header</code></td>
<td style="text-align: center;">0-1-0</td>
<td style="text-align: center;">-&gt;</td>
<td style="text-align: center;">0-1-1</td>
<td><code>div.header</code></td>
</tr>
<tr>
<td><code>ul &gt; li</code></td>
<td style="text-align: center;">0-0-2</td>
<td style="text-align: center;">-&gt;</td>
<td style="text-align: center;">0-0-2</td>
<td><code>ul li</code> (last read)</td>
</tr>
<tr>
<td><code>#main-header.large.on</code></td>
<td style="text-align: center;">1-2-0</td>
<td style="text-align: center;">&lt;-</td>
<td style="text-align: center;">1-1-1</td>
<td><code>div#main-header.header</code></td>
</tr>
</tbody>
</table>

Back to the example
Here's that original code.

```css
<style>
  .box { width: 50px; height: 50px; border: 1px solid black; }
  .orange { background-color: orange; }
  .yellow { background-color: yellow; border: 1px solid purple; }
</style>
<div class="box yellow"></div>
<div class="box orange"></div>
```

The .box rule has a score of 0-1-0. the .yellow rule has a score of 0-1-0, as well. That means last rule wins, so the element .box.yellow will have a solid purple border one pixel in width.
