---
title: HTML models
excerpt: HTML models that domonstrate hard-to-think layouts & effects.
last_modified_at: 2020-10-14
toc: true
classes: narrow
categories:
  - web
tags:
  - frontend
---

## Layout

### Zero-offset panel

Make a panel inside the `<body>` container without offsets or margins.

<p class="codepen" data-height="265" data-theme-id="dark" data-default-tab="css,result" data-user="ivanhjc" data-slug-hash="zVbrgp" data-preview="true" style="height: 265px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-pen-title="Zero-offset pane">
  <span>See the Pen <a href="https://codepen.io/ivanhjc/pen/zVbrgp">
  Zero-offset pane</a> by Ivan Huang (<a href="https://codepen.io/ivanhjc">@ivanhjc</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

See also: [Demo](/_demo/zero-offset-panel.html){:target="_blank"}

### Auto-expanding parent

Let a parent element expand as its children grows in number or size. The parent elements may grow in different directions and have different alignments, so there different implementation for different situations.

To expand vertically: The key is to use `min-height: <foo>` and and `height: auto` for the parent.

<p class="codepen" data-height="265" data-theme-id="dark" data-default-tab="css,result" data-user="ivanhjc" data-slug-hash="OeqNby" data-preview="true" style="height: 265px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-pen-title="Zero-offset pane">
  <span>See the Pen <a href="https://codepen.io/ivanhjc/pen/OeqNby">
  Zero-offset pane</a> by Ivan Huang (<a href="https://codepen.io/ivanhjc">@ivanhjc</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

See also: [Demo](/_demo/auto-expand-parent-vertical.html){:target="_blank"}

To expand horizontally: You can use `display: inline-block` for this purpose, but all the parent blocks will be aligned horizontally. To make them on separate lines use `float: left; clear: left;` instead.

<p class="codepen" data-height="265" data-theme-id="dark" data-default-tab="css,result" data-user="ivanhjc" data-slug-hash="YogqZo" data-preview="true" style="height: 265px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-pen-title="Zero-offset pane">
  <span>See the Pen <a href="https://codepen.io/ivanhjc/pen/YogqZo">
  Zero-offset pane</a> by Ivan Huang (<a href="https://codepen.io/ivanhjc">@ivanhjc</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

See also: [Demo](/_demo/auto-expand-parent-horizontal.html){:target="_blank"}

### Fixed scrollable panel

Make a panel which is fixed in position and scrollable when its content overflows.

<p class="codepen" data-height="265" data-theme-id="dark" data-default-tab="css,result" data-user="ivanhjc" data-slug-hash="zVbqPL" data-preview="true" style="height: 265px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-pen-title="Zero-offset pane">
  <span>See the Pen <a href="https://codepen.io/ivanhjc/pen/zVbqPL">
  Zero-offset pane</a> by Ivan Huang (<a href="https://codepen.io/ivanhjc">@ivanhjc</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

See also: [Demo](/_demo/fixed-scrollable-panel.html){:target="_blank"}

### Slide-in overlay

Make a panel overlaying another panel slide in/out by hovering on/off the other panel.

<p class="codepen" data-height="265" data-theme-id="dark" data-default-tab="css,result" data-user="ivanhjc" data-slug-hash="ZdPWRo" data-preview="true" style="height: 265px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-pen-title="Zero-offset pane">
  <span>See the Pen <a href="https://codepen.io/ivanhjc/pen/ZdPWRo">
  Zero-offset pane</a> by Ivan Huang (<a href="https://codepen.io/ivanhjc">@ivanhjc</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

See also: [Demo](/_demo/slide-in-overlay-on-hovering-4-drections.html){:target="_blank"}

### Slide-in overlay to carry

Make a panel overlaying another panel and carrying a child slide in/out by hovering on/off the other panel.

<p class="codepen" data-height="265" data-theme-id="dark" data-default-tab="css,result" data-user="ivanhjc" data-slug-hash="MMxyRX" data-preview="true" style="height: 265px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-pen-title="Zero-offset pane">
  <span>See the Pen <a href="https://codepen.io/ivanhjc/pen/MMxyRX">
  Zero-offset pane</a> by Ivan Huang (<a href="https://codepen.io/ivanhjc">@ivanhjc</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

See also: [Demo](/_demo/slide-in-overylay-on-hovering-carry-child.html){:target="_blank"}

### Slide-out overlay to unveil

Make a panel overlaying another panel slide out by hovering on the panel and reveal what's beneath.

<p class="codepen" data-height="265" data-theme-id="dark" data-default-tab="css,result" data-user="ivanhjc" data-slug-hash="YogqgX" data-preview="true" style="height: 265px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-pen-title="Zero-offset pane">
  <span>See the Pen <a href="https://codepen.io/ivanhjc/pen/YogqgX">
  Zero-offset pane</a> by Ivan Huang (<a href="https://codepen.io/ivanhjc">@ivanhjc</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

See also: [Demo](/_demo/slide-out-overlay-on-hovering-4-drections.html){:target="_blank"}