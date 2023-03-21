# 数据结构与算法

## 初级算法

### 数组

+ 数组的方法
  + unshift
  + reduce
  + Array.from
+ 双指针  
+ 正则
+ 反向引用

```js
// 1、除了使用相应API来引用分组，也可以在正则本身里引用分组。但只能引用之前出现的分组，即反向引用。
const regex = /\d{4}(-|\/|\.)\d{2}\1\d{2}/
const string1 = '2017-06-12'
const string2 = '2017/06/12'
const string3 = '2017.06.12'
const string4 = '2016-06/12'
console.log( regex.test(string1) ) // true
console.log( regex.test(string2) ) // true
console.log( regex.test(string3) ) // true
console.log( regex.test(string4) ) // false
```

+ 修饰符 g

```js
// 1、对exex和test的影响
const regex = /a/g;
console.log( regex.test('a'), regex.lastIndex );
console.log( regex.test('aba'), regex.lastIndex );
console.log( regex.test('ababc'), regex.lastIndex );
// => true 1
// => true 3
// => false 0

const regex = /a/;
console.log( regex.test('a'), regex.lastIndex );
console.log( regex.test('aba'), regex.lastIndex );
console.log( regex.test('ababc'), regex.lastIndex );
// => true 0
// => true 0
// => true 0
```

+ 运算符
+ 可选链运算符（?.）
+ 空值合并运算符（??）
+ 逻辑空赋值 (??=)

+ 按位非 (~)

```js
// 1、按位非运算符（~）将操作数的位反转。如同其他位运算符一样，它将操作数转化为 32 位的有符号整型。
// 2、通过 ～～ 取整
x = ~~(x / 10)
```

+ 按位与 (&)

```js
// 1、在两个操作数对应的二进位都为 1 时，该位的结果值才为 1，否则为 0
// 2、n & (n−1) 结果为把 n 的二进制位中的最低位的 1 变为 0 
let ret = 0
while (n) {
    n &= (n - 1)
    ret++
}
// 3、判断奇数 n & 1 === 1
```

+ 按位与赋值 (&=)

```js
Operator: x &= y
Meaning:  x  = x & y
```

+ 按位或 (|)

```js
// 1、在两个操作数对应的二进位有至少一个为 1 时，该位的结果值才为1，否则为 0
// 2、通过 | 0 取整，无论正负，只移除小数点部分（正数向下取整，负数向上取整）
x = (x / 10) | 0
// 3、通过 | 0 超过32位的整数转换结果不等于自身，可用作溢出判断
x | 0 === x ? true : false
```

+ 按位或赋值 (|=)

``` js
Operator: x |= y
Meaning:  x  = x | y
```

+ 按位异或 (^)

```js
// 1、在两个操作数对应的二进位有且只有一个为 1 时，该位的结果值才为 1， 否则为 0
```

+ 按位异或赋值 (^=)

```js
// 1、任何数和 0 做异或运算，结果仍然是原来的数
// 2、任何数和其自身做异或运算，结果是 0
// 3、异或运算满足交换律、结合率
var singleNumber = function(nums) { // 找出数组中只出现1次的数字，其它都出现2次
    let result = 0
    for (let i = 0; i < nums.length; i++) {
        // temp = temp ^ nums[i]
        result ^= nums[i]         
    }
    return result
}
```

+ 左移 (<<)

```js
// 1、左移操作符 (<<) 将第一个操作数向左移动指定位数，左边超出的位数将会被清除，右边将会补零。
// 2、移动任意数字 x 至左边 y 位，得出 x * 2 ** y。 
9 << 3; // 72
// 9 * 2³ = 9 * 8 = 72
```

+ 左移赋值 (<<=)

```js
x <<= y // x = x << y
```

+ 右移 (>>)

```js
// 1、右移操作符 (>>) 是将一个操作数按指定移动的位数向右移动，右边移出位被丢弃，左边移出的空位补符号位（最左边那位）。
9 >> 2; //  2
-9 >> 2; // -3

// 2、十进制去掉一位是 /10
// 位移是按二进制来计算的
// >>是去掉一位,就是 /2
// <<是增加一位,计算 *2
mid = L + (R - L) / 2
mid = L + ((R - L) >> 1)
```

+ 右移赋值 (>>=)

```js
x >>= y // x = x >> y
```

### 字符串

+ 递归反转字符串

```js
 /**
  * @param {character[]} s
  * @return {void} Do not return anything, modify s in-place instead.
  */
  var reverseString = function (s) {
    recursionReverse(s, 0, s.length - 1)
  }
  var recursionReverse = function (s, l, r) {
    if (l > r) {
    return
    }
    [s[l], s[r]] = [s[r], s[l]]
    recursionReverse(s, l++, r--)
  }
```

### 链表

+ 链表反向打印

```js
/**
* Definition for singly-linked list.
* function ListNode(val, next) {
*   this.val = (val===undefined ? 0 : val)
*   this.next = (next===undefined ? null : next)
* }
*/
var print = function (ListNode head) {
  recursionPrint(head)
}

var recursionPrint = function (ListNode head) {
  if (!head) {
    return
  }
  recursionPrint(head.next)
  console.log(head.val)
}
```
  
+ 尾递归

### 树

+ 递归
  + 找出重复的子问题（递推公式）
  + 确定终止条件

+ DFS
  + 前序遍历

  ```js
  // 根节点 -> 左子树 -> 右子树
  
  var TreeNode = function (val, left, right) { // 二叉树节点定义
    this.val = val === undefined ? 0 : val
    this.left = left === undefined ? null : left
    this.right = right === undefined ? null : left
  }
  // 方法一：递归
  // 时间复杂度 O(n)，每个节点最多被访问一次
  // 空间复杂度 O(n)，最坏情况下空递归最深达到 n 层，故最坏情况下空间复杂度为 O(n)
  // 空间复杂度不考虑返回值，因此空间复杂度主要取决于递归栈的深度
  var preOrder = function (root) {
    if (root === null) {
      return
    }
    console.log(root.val)
    preOrder(root.left)
    preOrder(root.right)
  }

  // 方法二：迭代 + 栈（先进后出）
  // 时间复杂度 O(n)，每个节点被遍历一次
  // 空间复杂度 O(n)，额外维护了一个栈
  var preOrder = function (root) {
    if (root === null) {
      return
    }
    const stack = [], ret = []
    stack.push(root)
    while (stack.length > 0) {
      const curr = stack.pop()
      ret.push(curr.val)
      if (curr.right) {
        stack.push(curr.right)
      }
      if (curr.left) {
        stack.push(curr.left)
      }
    }
  }
  ```

  + 中序遍历

  ```js
  // 左子树 -> 根节点 -> 右子树
  // 方法一：递归
  // 时间复杂度 O(n)
  // 空间复杂度 O(n)
  var inOrder = function (root) {
    if (root === null) {
      return
    }
    inOrder(root.left)
    console.log(root.val)
    inOrder(root.right)
  }

  // 方法二：迭代 + 栈（先进后出）
  // 时间复杂度 O(n)
  // 空间复杂度 O(n)
  var inOrder = function (root) {
    const stack = []
    const ret = []
    while (root || stack.length > 0) {
      while (root) {
        stack.push(root)
        root = root.left
      }
      const curr = stack.pop()
      ret.push(curr.val)
      root = curr.right    
    }
  }

  // 方法三：迭代 + 栈 + 单循环
  var inOrder = function (root) {
    const stack = [], ret = []
    while (stack.length || root) {
      if (root) {
        stack.push(root)
        root = root.left
      } else {
        const curr = stack.pop()
        ret.push(curr.val)
        root = curr.right
      }
    }
    return ret
  }
  ```

  + 后续遍历

  ```js
  // 左子树 -> 右子树 -> 根节点
  // 方法一：递归
  // 时间复杂度 O(n)
  // 空间复杂度 O(n)
  var postOrder = function (root) {
    if (root === null) {
      return
    }
    postOrder(root.left)
    postOrder(root.right)
    console.log(root.val)
  }

  // 方法二：迭代 + 栈（先进后出）
  // 时间复杂度 O(n)
  // 空间复杂度 O(n)
  var postOrder = function (root) {
    const stack = []
    let prev = null
    while (root || stack.length > 0) {
      while (root) {
        stack.push(root)
        root = root.left
      }
      const curr = stack.pop()
      if (!curr.right || curr.right === prev ) {
        cosole.log(curr.val)
        root = null
        prev = curr
      } else {
        stack.push(curr)
        root = curr.right
      }
    }
  }

  // 方法三：迭代 + 栈 + 不需要记录 prev
  var postOrder = function (root) {
    const stack = [], result = []
    while (root || stack.lenght) {
      while (root) {
        stack.push(root)
        if (root.left) {
          root = root.ledt
        } else {
          root = root.right
        }
      }
      const curr = stack.pop()
      result.push(curr.val)
      if (stack.lenght && curr === stack.at(-1).left) {
        root = stack.at(-1).right
      } else {
        root = null
      }
    }
    return ret
  }

  // 方法四：2次迭代 + 栈 （先进后出）
  // 时间复杂度 O(n)
  // 空间复杂度 O(n)
  var postOrder = function (root) {
    const stack = []
    const result= []
    stack.push(root)
    while (stack.lengh > 0) {
      const curr = stack.pop()
      result.push(currentNode.val)
      if (curr.left) {
         stack.push(curr.left)
      }
      if (curr.right) {
        root.push(root.right)
      }
    }
    while(result.length > 0) {
      console.log(result.pop())
    }
  }

  ```

  + BFS

  ```js
  // 一层一层往下访问
  
  // 方法一：递归
  var levelOrder = function (root) {
    const ret = [], level = 0
    bfs(root, ret, level)
    return ret
  }

  var bfs = function(root, ret, level) {
    if (!root) {
      return
    }
    if (ret.length === level) { // ret[level] === undifined
      ret.push([])
    }
    ret[level].push(root.val)
  
    bfs(root.left, ret, level + 1)
    bfs(root.right, ret, level + 1)
  }

  // 方法二：迭代 + 队列（先进先出）
  var levelOrder = function (root) {
    const queue = [], ret = []
    root && queue.push(root)
    while (queue.length > 0) {
      let size = queue.length
      const tmp = []
      while (size-- > 0) {
        const curr = queue.shift()
        tmp.push(curr.val)
        // console.log(curr.val)
        if (curr.left) {
          queue.push(curr.left)
        }
        if (curr.right) {
          queue.push(curr.right)
        }
      }
      ret.push(tmp)
    }
    return ret
  }

  ```
