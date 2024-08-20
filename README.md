# Svelte + Vite With custom root bug

Reproducing steps: 

Start the dev server `npm run dev`. And open the browser.
Displayed text should have backround-color yellow

Then open the file src/App.svelte in your favorite editor.

Change the background-color to something else, e.g. red.

```html
<style>
 .custom {
   background-color: yellow;
   /* background-color: red; */
 }
</style>
```

The background-color should be updated instantly in the browser.

But instead the background-color disappears.

Instead of serving only the css part, the whole App.svelte file is served as css style tag inside head.

```html
...
<style type="text/css" data-vite-dev-id="/home/svelte_bug/src/App.svelte?svelte&amp;type=style&amp;lang.css"><script>
</script>

<div class="custom">this is custom, run dev server, changte the background-color to red or green.</div>
<div class="custom">It should change background color, but it doesn't work on ubuntu</div>
<div class="custom">Restart dev server. Now background-color is ok. Until you change the color again.</div>

<style>
.custom {
  background-color: red;
}

</style>
</style>
</head>
<body>
...
```
