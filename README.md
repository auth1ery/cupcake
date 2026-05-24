# cupcake 🧁

a visual node-based javascript editor that lets you build programs by connecting blocks together, then compiles them to clean js!

## what it is

cupcake is a canvas-based tool where javascript concepts become draggable nodes with ports you connect together. string operations, math, loops, fetch calls, dom manipulation -- each one is a node. wire them up, hit run, and the console shows your output. hit compile and you get formatted javascript you can copy or download!

it runs entirely in the browser. no server, no accounts, no build step!

## keyboard shortcuts

| shortcut | action |
|---|---|
| ctrl/cmd + z | undo |
| ctrl/cmd + shift + z | redo |
| ctrl/cmd + c | copy selected |
| ctrl/cmd + v | paste |
| ctrl/cmd + a | select all |
| ctrl/cmd + f | find node on canvas |
| ctrl/cmd + b | quick-add node search |
| delete / backspace | delete selected node(s) |
| shift + drag canvas | draw a group frame |
| scroll | zoom in/out |
| escape | cancel pending connection or close search |
| ? | keyboard shortcut reference |

## running locally

cupcake is static html, css, and js. drop the files in any folder and open index.html (or app.html, index.html just redirects you to app.html anyways), or serve with anything:

```
npx serve .
python -m http.server
```

no dependencies to install.

## technical notes

- compiled code runs in a `Worker` created from a blob url, completely isolated from the main thread
- saves use indexeddb via a simple slot system
- wires are svg bezier curves drawn over the canvas in a single overlay element
- the js importer uses acorn to parse code into an ast, then maps ast nodes to cupcake node types
- prettier is loaded on demand from unpkg when you first compile
- the canvas is a 6000x6000px div with css transform for pan/zoom

## browser support

desktop only. chrome, firefox, and safari all work. mobile is blocked by design since the editor needs a pointer and enough screen real estate to be usable! sorry mobile guys :(
