# DXF Viewer

DXF viewer made using [dxf parser](https://github.com/skymakerolof/dxf) and [threejs](https://github.com/mrdoob/three.js/). It generates a threejs object that can be used in any scene. It also has some utility classes such as a merger and a snap helper.

### Installation

```shell
npm install three-dxf-viewer
```

## Example

To use it just initialize the main class and launch `getFromFile` or `getFrompath` methods.

```js

import { DXFViewer } from 'three-dxf-viewer';

// Suppose we have a font in our application 
let font = 'fonts/helvetiker_regular.typeface.json';

// Suppose we have a file input and a loading div
var file = event.target.files[0];

// Get all the geometry generated by the viewer
let dxf = await new DXFViewer().getFromFile( file, font );

// Add the geometry to the scene
scene.addDXF( dxf );

```

## Utilities

There are 2 utilities that can be used optionally with the viewer:

### Merger
Merger class can merge all entities to optimize drawing big DXF files.

```js
import { Merger } from 'three-dxf-viewer';

let dxf = await new DXFViewer().getFromPath( dxfFilePath, fontPath );

const mergedObject = new Merger().merge( dxf );

scene.add( mergedObject );

```


### Snaps
Snaps classes can store all the vertices in an efficient way. This allows to get the closest vertex to a point in the scene. This is useful for example to snap to the nearest vertex when drawing lines.

```js

import { SnapsHelper } from 'three-dxf-viewer';

let dxf = await new DXFViewer().getFromPath( dxfFilePath, fontPath );

let snaps = new SnapsHelper( dxf, renderer, scene, camera, controls );

```

## Development

For a more detailed explanation, there is an example on how to use the viewer on the source code in /example/index.js. Download it from github an launch it with:

```js
npm run dev
```
The application will be available on http://localhost:8080
