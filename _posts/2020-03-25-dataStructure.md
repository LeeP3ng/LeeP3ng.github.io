---
title: 前端常用的8种数据结构
date: 2020-03-25
updated: 2020-05-07
categories:
- data-structure
tags:
- data-structure
---

## 前言

数据结构在日常工作中还是比较常见的，例如对数组的操作，一些排序算法等等，掌握常用的数据结构能更快速的解决一些复杂的逻辑问题。

<!-- more -->

### 什么是数据结构：

**数据结构是计算机存储、组织数据的方式。对于特定的数据结构(比如数组)，有些操作效率很高(读某个数组元素)，有些操作的效率很低(删除某个数组元素)。程序员的目标是为当前的问题选择最优的数据结构。**

### 八种常用数据结构：

- 数组
- 栈
- 队列
- 链表
- 图
- 树
- 前缀树
- 哈希表

#### 数组

根据维度区分，有2种不同的数组：一维数组、多维数组(数组的元素为数组)

```javascript
let array1 = ['1', '2', '3'] // 一维数组
let array2 = [['1', '2'], ['2', '3']] // 二维数组(多维数组)
```

数组的基本操作:
- Insert - 在某个索引处插入元素
- Get - 读取某个索引处的元素
- Delete - 删除某个索引处的元素
- Size - 获取数组的长度

```javascript
let array = []
// Insert
array.push('1') // ["1"]

// Get
let item = array[0] // item: 1

// Delete
delete array[0] // true
console.log(array) // [empty]

// Size
let _size = array.length // size: 1
```

#### 栈

我们常用的Ctrl+z/command+z(撤回)，原理是：把之前的应用状态(限制个数)保存到内存中，最近的状态放到第一个，当我们按下撤回键的时候，取出最近的状态并应用。

栈中的元素采用LIFO (Last In First Out)，即后进先出。

栈的基本操作:
- Push — 在栈的最上方插入元素
- Pop — 返回栈最上方的元素，并将其删除
- isEmpty — 查询栈是否为空

```javascript
class Stack {
  constructor() {
    this.array = []
  }

  push(value) {
    this.array.push(value)
  }

  pop() {
    return this.array.pop()
  }

  isEmpty() {
    return !this.array.length
  }
}

let stack = new Stack()
// Push
stack.push('1') // ["1"]

// Pop
stack.pop() // []

// isEmpty
console.log(stack.isEmpty()) // true
```

#### 队列

队列(Queue)与栈类似，都是采用线性结构存储数据。它们的区别在于，栈采用LIFO方式，而队列采用先进先出，即FIFO(First in First Out)。

队列的基本操作:
- Enqueue — 在队列末尾插入元素
- Dequeue — 将队列第一个元素删除
- isEmpty — 查询队列是否为空

```javascript
class Queue {
  constructor(items) {
    this.items = items || []
  }

  // 在队列末尾插入元素
  enqueue(ele) {
    this.items.push(ele)
  }

  // 将队列第一个元素删除
  dequeue() {
    this.items.shift()
  }

  // 查询队列是否为空
  isEmpty() {
    return !this.items.length
  }
}

let queue = new Queue()

queue.enqueue('1') // Queue {items: Array(1)}

queue.dequeue() // Queue {items: Array(0)}

console.log(queue.isEmpty()) // true
```

#### 链表

链表(Linked List)也是线性结构，它与数组看起来非常像，但是它们的内存分配方式、内部结构和插入删除操作方式都不一样。链表是一系列节点组成的链，每一个节点保存了数据以及指向下一个节点的指针。链表头指针指向第一个节点，如果链表为空，则头指针为空或者为null。链表可以用来实现文件系统、哈希表和邻接表。

链表分为2种：单向链表、双向链表

链表的基本操作:
- InsertAtEnd — 在链表结尾插入元素
- InsertAtHead — 在链表开头插入元素
- Delete — 删除链表的指定元素
- DeleteAtHead — 删除链表第一个元素
- Search — 在链表中查询指定元素
- isEmpty — 查询链表是否为空

#### 图

图(graph)由多个节点(vertex)构成，节点之间阔以互相连接组成一个网络。(x, y)表示一条边(edge)，它表示节点x与y相连。边可能会有权值(weight/cost)。

图分为两种：无向图、有向图

在编程语言中，图有可能有以下两种形式表示：邻接矩阵(Adjacency Matrix)、邻接表(Adjacency List)

遍历图有两周算法：广度优先搜索(Breadth First Search)、深度优先搜索(Depth First Search)

#### 树

树(Tree)是一个分层的数据结构，由节点和连接节点的边组成。树是一种特殊的图，它与图最大的区别是没有循环。

树有很多分类：
- N叉树(N-ary Tree)
- 平衡树(Balanced Tree)
- 二叉树(Binary Tree)
- 二叉查找树(Binary Search Tree)
- 平衡二叉树(AVL Tree)
- 红黑树(Red Black Tree)
- 2-3树(2–3 Tree)

二叉树和二叉查找树是最常用的树。

#### 前缀树

前缀树(Prefix Trees或者Trie)与树类似，用于处理字符串相关的问题时非常高效。它可以实现快速检索，常用于字典中的单词查询，搜索引擎的自动补全甚至IP路由。

#### 哈希表

哈希(Hash)将某个对象变换为唯一标识符，该标识符通常用一个短的随机字母和数字组成的字符串来代表。哈希可以用来实现各种数据结构，其中最常用的就是哈希表(hash table)。

哈希表通常由数组实现。

```javascript
// 创建构造函数HashTable
function HashTable() {
  // 初始化哈希表的记录条数size
  var size = 0

  // 创建对象用于接受键值对
  var res = {}

  // 添加关键字，无返回值
  this.add = function (key, value) {
    //判断哈希表中是否存在key，若不存在，则size加1，且赋值
    if (!this.containKey(key)) {
      size++
    }

    // 如果之前不存在，赋值； 如果之前存在，覆盖。
    res[key] = value
  }

  // 删除关键字, 如果哈希表中包含key，并且delete返回true则删除，并使得size减1
  this.remove = function (key) {
    if (this.containKey(key) && (delete res[key])) {
      size--
    }
  }

  // 哈希表中是否包含key，返回一个布尔值
  this.containKey = function (key) {
    return (key in res)
  }

  // 哈希表中是否包含value，返回一个布尔值
  this.containValue = function (value) {
    // 遍历对象中的属性值，判断是否和给定value相等
    for (var prop in res) {
      if (res[prop] === value) {
        return true
      }
    }
    return false
  }

  // 根据键获取value,如果不存在就返回null
  this.getValue = function (key) {
    return this.containKey(key) ? res[key] : null
  }

  // 获取哈希表中的所有value, 返回一个数组
  this.getAllValues = function () {
    var values = []
    for (var prop in res) {
      values.push(res[prop])
    }
    return values
  }

  // 根据值获取哈希表中的key，如果不存在就返回null
  this.getKey = function (value) {
    for (var prop in res) {
      if (res[prop] === value) {
        return prop
      }
    }
    // 遍历结束没有return，就返回null
    return null
  }

  // 获取哈希表中所有的key,返回一个数组
  this.getAllKeys = function () {
    var keys = []
    for (var prop in res) {
      keys.push(prop)
    }
    return keys
  }

  // 获取哈希表中记录的条数，返回一个数值
  this.getSize = function () {
    return size
  }

  // 清空哈希表，无返回值
  this.clear = function () {
    size = 0
    res = {}
  }
}
```

哈希表的性能取决于3个指标：哈希函数、哈希表的大小、哈希冲突处理方式

### 持续更新...