# React学习第二天

## 组件的生命周期

>
  每个组件都有生命周期的方法,可以提供给你进行重写,如果你对objec-c的命名方式比较熟悉的话,你会看到熟悉的willXX,didXxx类似的方法.

组件的生命周期可分成三个状态：
* Mounting：已插入真实 DOM
* Updating：正在被重新渲染
* Unmounting：已移出真实 DOM


## Mounting

以下这些方法,是在插入dom操作之前会被调用,顺序分别是:

* constructor()
* componentWillMount()
* render()
* componentDidMount()

实际上,在constructor方法之后,还会执行两个方法,分别是:

* getDefaultProps
* getInitialState

这两个方法是定义 对象方法


## Updating

>
    组件中的值或者状态的改变,都会引起updating事件的发生, 这些方法都是在render发生时调用

按顺序列出:

* componentWillReceiveProps()
 当属性值改变时,将会调用这个方法,但初始化和setState时不会调用,只有两次render时,dom结构发生变化时,才会被调用

* shouldComponentUpdate()
再次render时,这个方法会检测state和props是否有改变,判断都在这里

* componentWillUpdate()
* render()
* componentDidUpdate()

## Unmounting
componentWillUnmount()
