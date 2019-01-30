### sigma.js
---
https://github.com/jacomyal/sigma.js

```json
{
  "nodes": [
    {
      "id": "n0",
      "label": "A node",
      "x": 0,
      "y": 0,
      "size": 3
    }.
    {
      "id": "n1",
      "label": "Another node",
      "x": 3,
      "y": 1,
      "size": 2
    },
  ],
  "edges": [
    {
      "id": "e0",
      "source": "n0",
      "target": "n1"
    },
    {
      "id": "e1",
      "source": "n1",
      "target": "n2"
    },
    {
      "id": "e2",
      "source": "n2",
      "target": "n0"
    },
}
```

```css
#container{
  max-width: 400px;
  height: 400px;
  margin: auto;
}
```

```js
sigma.parsers.json('data.json', {
  container: 'container',
  settings: {
    defaultNodeColor: '#ec5148'
  }
})
```

```html
<div id="container"></div>
```

