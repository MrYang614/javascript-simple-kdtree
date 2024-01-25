### npm i

k-dimensions-tree k维分割树，用于大量数据情景下的空间搜索

## 选择这个库的原因
### 1. 优化每层的排序方法，构建树的事件复杂度压缩至 O(n*log(n))。
### 2. 仅搜索 distance 内的所有数据，不进行排序处理。
### 3. 支持动态插入和删除节点，在平衡度允许范围内不必对树进行重构。

```
const points = [
	{ z: 1, y: 2, x: 110 },
	{ z: 1, y: 2, x: 222 },
	{ z: 1, y: 2, x: 333 },
];

function distance(a, b) {
    var dx = a.x - b.x;
    var dz = a.z - b.z;
    return Math.sqrt(dx * dx + dz * dz);
}

const tree = new SimpleKDTree(points, distance, ["x", "z"]);

const searchTarget = {x:0,y:0,z:0}
const result = tree.nearest(searchTarget,300) //  [[Node, 110.00454536063498],[Node, 222.00225224082752]]

```