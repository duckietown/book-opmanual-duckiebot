
<!--
(test-overview)=
# Setup Graph (test)

```{seo}
:description: 
:keywords: 
```

```{needget}
- An initialized Duckiebot
---
- A working Duckiebot
```

```{figure} ../../_images/intro/filename.ext
:alt: 
:width: 75%
:name: 
:align: center

Description
```

```{testexpect}
do this
---
get this
```

-->

<!--
## Graph test

```{only} html
```{raw} html
<div style="max-width:1024px;margin:1rem auto">
  <div id="duckie-graph" style="height:560px;border:1px solid #e5e7eb;border-radius:14px;"></div>
  <div style="display:flex;gap:.5rem;justify-content:flex-end;margin-top:.5rem">
    <button id="dg-fit" style="padding:.4rem .7rem;border:1px solid #d1d5db;border-radius:8px;background:#fff;cursor:pointer">Fit</button>
    <button id="dg-reset" style="padding:.4rem .7rem;border:1px solid #d1d5db;border-radius:8px;background:#fff;cursor:pointer">Reset</button>
  </div>
</div>
-->

<!-- Dev: use CDN. Release: vendor to /_static/js/cytoscape.min.js and swap src -->

<!--
<script src="https://unpkg.com/cytoscape@3.28.1/dist/cytoscape.min.js"></script>
<script>
(function () {
  // Duckietown-ish palette
  const C = {
    yellow: '#fbbf24',
    yellowDark: '#f59e0b',
    edge: '#cbd5e1',
    edgeEmph: '#111827',
    text: '#111827',
    textOnYellow: '#0b0b0b'
  };

  // Elements — edit labels/URLs/positions to match your sketch
  const elements = [
    // Phase groups (compound nodes for subtle background grouping)
    { data: { id: 'phase-prepare',  label: 'Prepare'  } },
    { data: { id: 'phase-config',   label: 'Configure'} },
    { data: { id: 'phase-operate',  label: 'Operate'  } },
    { data: { id: 'phase-support',  label: 'Support'  } },

    // Nodes (assign parent to place them inside a phase)
    { data: { id: 'overview',  label: 'Start · Overview',       url: '#', parent: 'phase-prepare' }, position: { x: 120, y: 110 } },
    { data: { id: 'workspace', label: '1. Setup Workspace',      url: '#', parent: 'phase-prepare' }, position: { x: 360, y: 110 } },
    { data: { id: 'assemble',  label: '2. Assemble Duckiebot',   url: '#', parent: 'phase-prepare' }, position: { x: 600, y: 110 } },

    { data: { id: 'flash',     label: '3. Flash Image',          url: '#', parent: 'phase-config'  }, position: { x: 360, y: 240 } },
    { data: { id: 'network',   label: '4. Network Config',       url: '#', parent: 'phase-config'  }, position: { x: 600, y: 240 } },
    { data: { id: 'calib',     label: '5. Calibrate (camera & wheels)', url: '#', parent: 'phase-config'  }, position: { x: 360, y: 360 } },

    { data: { id: 'operate',   label: '6. Operate Robot',        url: '#', parent: 'phase-operate' }, position: { x: 600, y: 360 } },
    { data: { id: 'demos',     label: '7. Run Demos',            url: '#', parent: 'phase-operate' }, position: { x: 360, y: 480 } },

    { data: { id: 'trouble',   label: 'Troubleshooting',         url: '#', parent: 'phase-support' }, position: { x: 600, y: 480 } },
    { data: { id: 'advanced',  label: 'Advanced Ops',            url: '#', parent: 'phase-support' }, position: { x: 360, y: 600 } },

    // Edges (tune as needed)
    { data: { id: 'e1', source: 'overview',  target: 'workspace' } },
    { data: { id: 'e2', source: 'workspace', target: 'assemble'  } },
    { data: { id: 'e3', source: 'assemble',  target: 'flash'     } },
    { data: { id: 'e4', source: 'flash',     target: 'network'   } },
    { data: { id: 'e5', source: 'network',   target: 'calib'     } },
    { data: { id: 'e6', source: 'calib',     target: 'operate'   } },
    { data: { id: 'e7', source: 'operate',   target: 'demos'     } },
    { data: { id: 'e8', source: 'demos',     target: 'trouble'   } },
    { data: { id: 'e9', source: 'trouble',   target: 'advanced'  } }
  ];

  const cy = cytoscape({
    container: document.getElementById('duckie-graph'),
    elements,
    layout: { name: 'preset' },
    wheelSensitivity: 0.2,
    minZoom: 0.5,
    maxZoom: 2.0,
    style: [
      // Phase backgrounds
      {
        selector: ':parent',
        style: {
          'background-color': '#f9fafb',
          'shape': 'round-rectangle',
          'padding': '24px',
          'border-width': 1,
          'border-color': '#e5e7eb',
          'label': 'data(label)',
          'text-valign': 'top',
          'text-halign': 'left',
          'text-margin-y': -10,
          'text-margin-x': 8,
          'font-size': 12,
          'color': '#6b7280'
        }
      },
      // Nodes
      {
        selector: 'node[!parent]',
        style: {
          'shape': 'round-rectangle',
          'background-color': C.yellow,
          'border-width': 2,
          'border-color': C.yellowDark,
          'label': 'data(label)',
          'text-wrap': 'wrap',
          'text-max-width': 200,
          'text-valign': 'center',
          'text-halign': 'center',
          'font-size': 14,
          'color': C.textOnYellow,
          'padding': '12px',
          'width': 'label',
          'height': 'label'
        }
      },
      // Edges
      {
        selector: 'edge',
        style: {
          'width': 2,
          'line-color': C.edge,
          'curve-style': 'bezier',
          'target-arrow-shape': 'triangle',
          'target-arrow-color': C.edge
        }
      },
      // Hover emphasis
      {
        selector: 'node.hovered',
        style: {
          'background-color': '#fde68a',
          'border-color': C.yellowDark
        }
      },
      {
        selector: 'edge.emph',
        style: {
          'line-color': C.edgeEmph,
          'target-arrow-color': C.edgeEmph,
          'width': 3
        }
      }
    ]
  });

  // Hover interactions
  cy.on('mouseover', 'node', (evt) => {
    const n = evt.target;
    n.addClass('hovered');
    n.connectedEdges().addClass('emph');
    document.getElementById('duckie-graph').style.cursor = 'pointer';
  });
  cy.on('mouseout', 'node', (evt) => {
    const n = evt.target;
    n.removeClass('hovered');
    n.connectedEdges().removeClass('emph');
    document.getElementById('duckie-graph').style.cursor = 'default';
  });

  // Click to open URLs
  cy.on('tap', 'node', (evt) => {
    const url = evt.target.data('url');
    if (url && typeof url === 'string') {
      window.open(url, '_blank', 'noopener');
    }
  });

  // Controls
  const initialZoom = cy.zoom();
  const initialPan  = cy.pan();
  document.getElementById('dg-fit').addEventListener('click', () => cy.fit(undefined, 20));
  document.getElementById('dg-reset').addEventListener('click', () => { cy.zoom(initialZoom); cy.pan(initialPan); });

  // First-paint fit & lightweight responsiveness
  setTimeout(() => cy.fit(undefined, 24), 0);
  window.addEventListener('resize', (() => {
    let t; return () => { clearTimeout(t); t = setTimeout(() => cy.fit(undefined, 24), 120); };
  })());
}());
</script>
```

-->