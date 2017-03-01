# REACT FOR JSX

## 第一天

```
<script src="../../build/react.js"></script>
    <script src="../../build/react-dom.js"></script>
    <script src="../../build/browser.min.js"></script>
```

index.html中的三个引入文件分别的作用:

* react.js

    react核心库

* react-dom.js

    react的dom解析库

* browser.min.js

   jsx语言转化为js语言的转化库,`Browser.js` 的作用是将`JSX`语法转为`JavaScript` 语法，这一步很消耗时间，实际上线的时候，应该将它放到服务器完成。


**疑问?**
>怎么放到服务器上,浏览器就不需要加载了



## react语法

### 简介

>React 使用 JSX 来替代常规的 JavaScript。
JSX 是一个看起来很像 XML 的 JavaScript 语法扩展。


我们不需要一定使用 JSX，但它有以下优点：

* JSX 执行更快，因为它在编译为 JavaScript 代码后进行了优化。
* 它是类型安全的，在编译过程中就能发现错误。
* 使用 JSX 编写模板更加简单快速。

`ReactDOM.render` 是 React 的最基本方法，用于将模板转为 HTML 语言，并插入指定的 DOM 节点。

render函数有两个参数,第一个参数代表虚拟节点,即你要插入的html节点代码,第二个参数是最基本的html的dom节点对象,可以通过docoment获取.

## jsx语法

* html与js混写

HTML 语言直接写在 JavaScript 语言之中，不加任何引号，这就是 JSX 的语法，它允许 HTML 与 JavaScript 的混写

第三个例子是html与js混写

**注**
第三个例子中,map方法是react的封装方法,map将会遍历回调function

* JSX 允许直接在模板插入 JavaScript 变量。

JSX 允许直接在模板插入 JavaScript 变量。如果这个变量是一个数组，则会展开这个数组的所有成员

见例子四:

```
var arr = [
            <h1>Hello world!</h1>,
    <h2>React is great language</h2>,
    ];
    ReactDOM.render(
    <div>{arr}</div>,
            document.getElementById('example4')
    );
```

* 我们可以在 JSX 中使用 JavaScript 表达式。表达式写在花括号 {} 中。实例如下：


```
var a = 3
ReactDOM.render(
    <div>
      <h1>{1+a}</h1>
    </div>
    ,
    document.getElementById('example')
);
```

* 不能使用 `if else` 语句,conditional表达式代替

```
var i = 1;
ReactDOM.render(
    <div>
      <h1>{i == 1 ? 'True!' : 'False'}</h1>
    </div>
    ,
    document.getElementById('example')
);
```


* jsx代码可以放在独立文件

index.html:

 ```
 <body>
      <div id="example"></div>
    <script type="text/babel" src="helloworld_react.js"></script>
    </body>
```

helloworld_react.js :

```
ReactDOM.render(
     <h1>Hello, world!</h1>,
     document.getElementById('example')
   );
   ```


* React 推荐使用内联样式,支持样式设置。

示例:
```
var myStyle = {
       fontSize: 100,
       color: '#FF0000'
   };
   ReactDOM.render(
       <h1 style = {myStyle}>菜鸟教程</h1>,
       document.getElementById('example')
   );
   ```


## HTML 标签 vs. React 组件

 * React 可以渲染 HTML 标签 (strings) 或 React 组件 (classes)。

 要渲染 HTML 标签，只需在 JSX 里使用小写字母的标签名。
 ```
 var myDivElement = <div className="foo" />;
 ReactDOM.render(myDivElement, document.getElementById('example'));
 ```

 要渲染 React 组件，只需创建一个大写字母开头的本地变量。
 ```
 var MyComponent = React.createClass({/*...*/});
 var myElement = <MyComponent someProperty={true} />;
 ReactDOM.render(myElement, document.getElementById('example'));
 ```

 React 的 JSX 使用大、小写的约定来区分本地组件的类和 HTML 标签。

 **注意**:

 >由于 JSX 就是 JavaScript，一些标识符像 class 和 for 不建议作为 XML 属性名。作为替代，React DOM 使用 className 和 htmlFor 来做对应的属性。


# react组件

## 如何通过js封装成标签组件使用(基于jsx)

    function Welcome(props) {
        return <h1>Hello, {props.name}</h1>;
    }

相当于:

    var Welcome = React.createClass(
    {
    render:function(){
        return <h1>Hello, {props.name}</h1>;
    }
    });


使用js的方式封装的组件:

    ReactDOM.render(<Welcome name="sam"/>,docment.getElementById('example'));

 > React 允许将代码封装成组件（component），然后像插入普通 HTML 标签一样，在网页中插入这个组件。


 React.createClass 方法就用于生成一个组件类,所有组件必须要有render方法,用于输出组件.

 也可以通过es6的方式,生成组件:

 eg:

    class Greeting extends React.Component {
    render() {
     return <h1>Hello, {this.props.name}</h1>;
        }
    }

**注意**

>组件类的第一个字母必须大写，否则会报错，比如HelloMessage不能写成helloMessage。另外，组件类只能包含一个顶层标签，否则也会报错。

eg:

```
var HelloMessage = React.createClass({
  render: function() {
    return <h1>
      Hello {this.props.name}
    </h1><p>
      some text
    </p>;
  }
});
```


上面代码会报错，因为HelloMessage组件包含了两个顶层标签：h1和p.


组件的用法与原生的 HTML 标签完全一致，可以任意加入属性，比如 <HelloMessage name="John"> ，就是 HelloMessage 组件加入一个 name 属性，值为 John。组件的属性可以在组件类的 this.props 对象上获取，比如 name 属性就可以通过 this.props.name 读取。上面代码的运行结果如下。


示例:
```<script type="text/babel">
       var HelloMessage = React.createClass({
           render: function() {
               return <h1>Hello {this.props.name} ,className is {this.props.className}</h1>;
           }
       });

       ReactDOM.render(
       <HelloMessage name="sam" className="class1"/>,
               document.getElementById('example')
       );


   </script>
   ```


**注意**

> 添加组件属性，有一个地方需要注意，就是 class 属性需要写成 className ，for 属性需要写成 htmlFor ，这是因为 class 和 for 是 JavaScript 的保留字。


## this.props.children

this.props 对象的属性与组件的属性一一对应，但是有一个例外，就是 this.props.children 属性。它表示组件的所有子节点.


eg:
```
var NotesList = React.createClass({
  render: function() {
    return (
      <ol>
      {
        React.Children.map(this.props.children, function (child) {
          return <li>{child}</li>;
        })
      }
      </ol>
    );
  }
});

ReactDOM.render(
  <NotesList>
    <span>hello</span>
    <span>world</span>
  </NotesList>,
  document.body
);
```



> React 提供一个工具方法 React.Children 来处理 this.props.children 。

我们可以用 React.Children.map 来遍历子节点，而不用担心 this.props.children 的数据类型是 undefined 还是 object。更多的 React.Children 的方法，请[参考官方文档](https://facebook.github.io/react/docs/top-level-api.html#react.children)。


## PropTypes

> 组件的属性可以接受任意值，字符串、对象、函数等等都可以。有时，我们需要一种机制，验证别人使用组件时，提供的参数是否符合要求。

组件类的PropTypes属性，就是用来验证组件实例的属性是否符合要求.

我们来看一个例子,我们给一个组件的属性加一个必填的校验,并且必须是字符串,我让校验故意不过,看会出现什么:

eg:
```
var MyTitle = React.createClass({
  propTypes: {
    title: React.PropTypes.string.isRequired,
  },

  render: function() {
     return <h1> {this.props.title} </h1>;
   }
});


var data = 123;

ReactDOM.render(
  <MyTitle title={data} />,
  document.body
);
```


这样一来，title属性就通不过验证了。控制台会显示一行错误信息。

```
Warning: Failed propType: Invalid prop `title` of type `number` supplied to `MyTitle`, expected `string`.
   warning @ react.js:19287
   checkPropTypes @ react.js:10366
   validatePropTypes @ react.js:10385
   createElement @ react.js:10419
   (anonymous) @ embedded:51
   transform.run @ browser.min.js:3
   exec @ browser.min.js:3
   runScripts @ browser.min.js:3
   ```


 如下所示:

 ![img](http://ojnkdvkci.bkt.clouddn.com/bwm9os66vkxqsn1zt0ewntn587)



那么问题来了,我想要做一个表单校验的组件,对手机号码格式进行校验,看了一会,感觉还要用好多我不会的技术.这个问题放到最后吧.









