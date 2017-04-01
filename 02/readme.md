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


## 第三天的计划

1. 组件ajax
2. react 表单与事件
3. 组件间传值与更新值



## React与React Native 的区别


> 刚开始学习React，对于React和React Native弄的比较蒙逼，原来React和RN不是一个东西,之前两天还一直在学习React，以为学习了React就可以开始混合app，其实不对，React是用来开发web的,也包括mobileWeb。


React是一种思想，Facebook对于Web Components的理解与实现。其中ReactJS是Web端，React Native是iOS/Android端。值得注意的是React Native写的应用是Native App，而不是Hybrid App。最后React其理念是“Learn once, write anywhere”，所以目前Web和Mobile端要写两套代码。

也就是说，前几天的学习，是对React.js的学习，只是学习了他的web的知识。

那现在开始学习React Native，以快速可以开发app为目的。


# React Native

> Learn once, write anywhere

[React官网]

[RN官网]


## Installing Dependencies
- Node.js
- Watchman
- the React Native command line interface, and Xcode.

We recommend installing Node and Watchman using Homebrew. Run the following commands in a Terminal after installing Homebrew:
`brew install node
`brew install watchman

Watchman is a tool by Facebook for watching changes in the filesystem. It is highly recommended you install it for better performance.

## The React Native CLI
Node.js comes with npm, which lets you install the React Native command line interface.
Run the following command in a Terminal:

`npm install -g react-native-cli
If you get an error like Cannot find module 'npmlog', try installing npm directly: ` curl -0 -L https://npmjs.org/install.sh | sudo sh.

Xcode
The easiest way to install Xcode is via the Mac App Store. Installing Xcode will also install the iOS Simulator and all the necessary tools to build your iOS app.

Testing your React Native Installation
Use the React Native command line interface to generate a new React Native project called "AwesomeProject", then run react-native run-ios inside the newly created folder.
`react-native init AwesomeProject
`cd AwesomeProject
`react-native run-ios

You should see your new app running in the iOS Simulator shortly.
react-native run-ios is just one way to run your app. You can also run it directly from within Xcode or Nuclide.


如果在初始化项目时，发现无法下载React native相关的依赖，那就是天朝的网络原因了，这个时候执行：

`yarn config set registry https://registry.npm.taobao.org`

将官网的yarn仓库地址更换成淘宝的源。


## 在AwesomeProject这个项目中