serialize-wavefront-obj
=======================
### Wavefront OBJ serializer

Serializes a mesh to a [Wavefront OBJ](http://en.wikipedia.org/wiki/Wavefront_.obj_file) string.

Supports vertex normals and UV coordinates. Doesn't support material libraries, nor multiple meshes embedded in the same file.

Install
-------

```bash
$ npm install serialize-wavefront-obj
```

Example
-------

```javascript
var serializeOBJ = require('serialize-wavefront-obj');

var mesh = {
  positions: [
    [-1.0, 0.0, 0.0],
    [ 0.0, 1.0, 0.0],
    [ 1.0, 0.0, 0.0]
  ],
  cells: [
    [0, 1, 2]
  ]
};

var str = serializeOBJ(mesh.cells, mesh.positions/*, vertexNormals */);
console.log(str);
/*
v -1 0 0
v 0 1 0
v 1 0 0
f 1// 2// 3//
*/
```

Usage
-----

### `serializeOBJ(cells, positions[, vertexNormals, vertexUVs, faceNormals, faceUVs, name])`

* `cells` mesh cells / faces
* `positions` mesh vertex positions
* `vertexNormals` optional vertex normals.
* `vertexUVs` optional vertex UV coordinates.
* `faceNormals` optional array formated like `cells` that indicates the normal indices. Defaults to `cells` if falsy and `vertexNormals` is provided.
* `faceUVs` optional array formated like `cells` that indicates the UV indices. Defaults to `cells` if falsy and `vertexUVs` is provided.
* `name` optional mesh name. If specified outputs an `o name` line at the beginning of the file.

Argument position is mandatory. Provide falsy values for optional args you do not wish to use.