### 深度优先遍历和广度优先遍历

深度优先遍历是指从某个顶点出发，首先访问这个顶点，然后找出刚访问这个结点的第一个未被访问的邻结点，然后再以此邻结点为顶点，继续找它的下一个顶点进行访问。重复此步骤，直至所有结点都被访问完为止。

```js
//1.深度优先遍历的递归写法
function deepTraversal(node) {
  let nodes = []
  if (node != null) {
    nodes.push[node]
    let childrens = node.children
    for (let i = 0; i < childrens.length; i++) deepTraversal(childrens[i])
  }
  return nodes
}

//2.深度优先遍历的非递归写法
function deepTraversal(node) {
  let nodes = []
  if (node != null) {
    let stack = [] //同来存放将来要访问的节点
    stack.push(node)
    while (stack.length != 0) {
      let item = stack.pop() //正在访问的节点
      nodes.push(item)
      let childrens = item.children
      for (
        let i = childrens.length - 1;
        i >= 0;
        i-- //将现在访问点的节点的子节点存入stack，供将来访问
      )
        stack.push(childrens[i])
    }
  }
  return nodes
}
```

广度优先遍历是从某个顶点出发，首先访问这个顶点，然后找出刚访问这个结点所有未被访问的邻结点，访问完后再访问这些结点中第一个邻结点的所有结点，重复此方法，直到所有结点都被访问完为止。

```js
//3.广度优先遍历的递归写法
function wideTraversal(node) {
  let nodes = [],
    i = 0
  if (node != null) {
    nodes.push(node)
    wideTraversal(node.nextElementSibling)
    node = nodes[i++]
    wideTraversal(node.firstElementChild)
  }
  return nodes
}

//4.广度优先遍历的非递归写法
function wideTraversal(node) {
  let nodes = [],
    i = 0
  while (node != null) {
    nodes.push(node)
    node = nodes[i++]
    let childrens = node.children
    for (let i = 0; i < childrens.length; i++) {
      nodes.push(childrens[i])
    }
  }
  return nodes
}
```

### 两者的区别

对于算法来说 无非就是时间换空间 空间换时间

- 深度优先不需要记住所有的节点, 所以占用空间小, 而广度优先需要先记录所有的节点占用空间大
- 深度优先有回溯的操作(没有路走了需要回头)所以相对而言时间会长一点
- 深度优先采用的是堆栈的形式, 即先进后出
- 广度优先则采用的是队列的形式, 即先进先出
