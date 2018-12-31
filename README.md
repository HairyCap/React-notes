# React-notes

## React

### 针对 Web 的 React 由 React Core 库和 ReactDOM 库组成。React Core 库旨在通过使用 JavaScript 和 JSX(可选)，构建和共享可组合的 UI 组件。另一方面，要在浏览器中使用 React，可以使用 ReactDOM 库，该库拥有用于 DOM 渲染与服务器端渲染的方法

## Create react elements

- pure JS

  ```js
  import React, { Component } from "react";
  class HelloWorld extends Component {
    render() {
      return React.createElement("h1", null, "Hello World!");
      //React.createElement(tagNme,property,child or innerText)
    }
  }
  ```

- JSX
  ```jsx
  import React,{ Component } from 'react'
  class HelloWorld extends Component {
    render(){
      return(
        <h1>Hello World</h1>
        {/*<h1>Hello World</h1>*/}
      )
    }
  }
  ```

## Tips:

### React 是声明式(Declarative)的，它只是一个视图或 UI 层

### React 使用组件(Component)，并通过 ReactDOM.render()方法对其进行渲染。

### React 组件类通过 class 创建，只有 render()方法是必要的

### React 组件是可重用的，并且拥有不可变的属性，可以通过 this.props.NAME 来访问它们

### 在 React 中使用纯 JavaScript 来编写和组合 UI

### 进行 React 开发时不必非得使用 JSX，JSX 是可选的

### 可以使用 createElement()的第三个以及后续的参数来嵌套 React 元素

### 从自定义组建类创建元素( <HelloWorld /> )

### 使用属性修改结果元素(this.props)

### 可以传递属性给子元素({ ...this.props })

## React 和 JSX 的陷阱

- JSX 组件标签的结束斜杠(/)是必须的

  `<HelloWorld />` 不能写成 `<HelloWorld>`

- 特殊字符

  &copy; 版权符号 `&copy;`

  &mdash; 破折号 `&mdash;`

  &ldquo; 引号 `&ldquo;`

  可以在`<span>`或`<input>`标签的字符串属性中渲染这些字符，如

  ```html
  <span>&copy;&mdash;&ldpuo;</span>
  <input value='&copy;&mdash;&ldpuo;'/>
  ```

  但是不能在 JSX 中动态的输出 HTML 实体，将得到直接的文本输出(&copy;&mdash;&ldpuo;)

  ```JSX
  var specialChars = '&copy;&mdash;&ldpuo;'
  <span>{specialChars}</span>
  <input value={spacialChars}/>
  ```

- data- 属性

  data-前缀的属性将被添加到 DOM 节点，但是将 DOM 当作数据库或本地储存使用。

- style 属性

  JSX 中的 style 属性需要传递 JS 对象而不是字符串，主要原因为当视图发生变化时，使用对象，React 渲染的更快

  CSS 属性的命名使用小驼峰(camelCase)风格。

- class 和 for

  React 和 JSX 接收除了 class 和 for 这两个 ECMAScript 保留字以外的任标准的 HTML 属性。React 使用 className 和 htmlFor 来代替它们

- 布尔类型(boolean)的属性值

  disabled,required,checked,autofocus,readOnly 这些属性只能在表单元素上使用。属性值必须设置在 JS 表达式中( in {} ) 如{ false },{ true }，不能设置成字符串'false','true'。

  非空字符串被 JavaScript 认为 true,如'false'。

  JavaScript 一共有 6 个假(false)值

  ```js
  false;
  0;
  ("");
  null;
  undefined;
  NaN;
  ```

## Tips:

### JSX 只是 React 的 createElement()方法的语法糖。

### 应该使用 className 和 htmlFor 来替换标准的 class 和 for 属性

### style 属性的值应该是 JavaScript 对象

### 三目运算符 (?:) 和 IIFE 是实现 if/else 语句的最佳方法
