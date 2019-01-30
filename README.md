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
    },
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

sigma.parsers.gexf(
  'path/to/les-miserables.gexf',
  {
    container: 'sigma-container'
  },
  function(s){
  }
);

sigma.classes.graph.addMethod('neighbors', function(nodeId){
  var k,
    neighbors = {},
    index = this.allNeighborsIndex[nodeId] || {};
  for (k in index)
    neighnors[k] = this.nodesIndex[k];
    return neighbors;
});
sigma.parser.gexf(
  'path/to/les-miserables.gexf',
  {
    container: 'sigma-container'
  },
  function(s){
    s.graph.nodes().forEach(function(n){
      n.originalColor = n.color;
    });
    s.graph.edges().forEach(function(e){
      e.originalColor = e.color;
    });
    s.bind('callNode', function(e){
      var nodeId = s.graph.neighbors(nodeId);
        toKeep = s.graph.neighbors(nodeId);
      toKeep[nodeId] = e.data.node;
      s.graph.nodes().forEach(function(n){
        if(toKeep[n.id])
          n.color = n.originalColor;
        else
          n.color = '#eee';
      });
      s.graph.edges().forEach(function(e){
        if(toKeep[e.source] && toKeep[e.target])
          e.color = e.oroginalColor;
        else
          e.color = '#eee';
      });
      s.refresh();
    });
    s.bind('', function(e){
      s.graph.nodes().forEach(function(n){
        n.color = n.originalColor;
      });
      s.graph.nodes().forEah(function(e){
        e.color = e.originalColor;
      });
      s.refresh();
    });
  }
);
```

```html
<div id="container"></div>
```

