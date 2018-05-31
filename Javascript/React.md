## React

### React基础

#### Props和state

1. 关于 setState() 这里有三件事情需要知道
- 不要直接更新状态
- 状态更新可能是异步的
- 状态更新合并

2. React是数据自顶向下流动/单向数据流

#### 事件处理

1. 在 React 中另一个不同是你不能使用返回`false`的方式阻止默认行为。你必须明确的使用`preventDefault`

#### React理念

1. 把 UI 划分出组件层级
2. 用 React 创建一个静态版本
3. 定义 UI 状态的最小(但完整)表示
4. 确定你的 State 应该位于哪里
5. 添加反向数据流

### React进阶

#### 深入 JSX

1. React 必须声明
2. 支持点表示法
```javascript
const MyComponents = {
  DatePicker: function DatePicker(props) {
    return <div>Imagine a {props.color} datepicker here.</div>;
  }
}

function BlueDatePicker() {
  return <MyComponents.DatePicker color="blue" />;
}
```

3. 组件首字母必须大写
4. 组件支持在运行时选择类型

```javascript
const components = {
  photo: PhotoStory,
  video: VideoStory
};

function Story(props) {
  const SpecificStory = components[props.storyType];
  return <SpecificStory story={props.story} />;
}
```

5. 使用 JavaScript 表达式，已{}
6. 字符串常量
7. 没有给属性传值，它默认为 true
8. 支持...来扩展属性
9. 子代：`props.children`(标签中的内容：字符串，表达式、函数都可以)
10. 子代是false、null、undefined 和 true 是有效的，但它们不会直接被渲染
    - **值得注意的是，JavaScript 中的一些 “falsy” 值(比如数字0)，它们依然会被渲染**


#### PropTypes

1. `propTypes` 只在开发模式下进行检查
2. `PropTypes`可以来控制props的类型
3. 子代类型的控制：`PropTypes.element`
4. `defaultProps`定义Props属性默认值
5. 类型检查发生在 `defaultProps` 赋值之后，类型检查也会应用在 `defaultProps` 上面

#### Refs

1. Refs 提供了一种方式，用于访问在 render 方法中创建的 DOM 节点或 React 元素
2. 何时使用 Refs:
    - 处理焦点、文本选择或媒体控制。
    - 触发强制动画。
    - 集成第三方 DOM 库
3. 使用 React.createRef() 创建 refs，通过 ref 属性来获得 React 元素
4. 访问ref的值：
    - 当 ref 属性被用于一个普通的 HTML 元素时，React.createRef() 将接收底层 DOM 元素作为它的 current 属性以创建 ref
    - 当 `ref` 属性被用于一个自定义类组件时，ref 对象将接收该组件已挂载的实例作为它的 `current`
	- PS：**这种方法仅对 class 声明的 CustomTextInput 有效**
    - 你不能在函数式组件上使用 ref 属性，因为它们没有实例

5. Ref 转发使组件可以像暴露自己的 ref 一样暴露子组件的 ref
6. React 将在组件挂载时将 DOM 元素传入ref 回调函数并调用，当卸载时传入 null 并调用它。ref 回调函数会在 componentDidMout 和 componentDidUpdate 生命周期函数前被调用
7. 不建议 string 类型的 ref 属性

**ps:不要在组件的render方法中访问ref引用，render方法只是返回一个虚拟dom，这时组件不一定挂载到dom中或者render返回的虚拟dom不一定会更新到dom中**

#### 非受控组件和受控组件

1. 要编写一个非受控组件，而非为每个状态更新编写事件处理程序，你可以 使用 ref 从 DOM 获取表单值
2. 使用非受控组件时，如果希望 React 可以为其指定初始值，但不再控制后续更新可以指定 defaultValue 属性而不是 value
3. HTML表单元素与React中的其他DOM元素有所不同,因为表单元素生来就保留一些内部状态
4. 受控组件主要依靠`state`和`value`来处理数组
5. 非受控组件主要依靠ref来处理数据

#### React性能优化

1. 使用生产版本
2. shouldComponentUpdate应用
3. 不会突变的数据的力量
4. 使用不可突变的数据结构

#### 不适用ES6

1. 如果使用 class 关键字创建组件，可以直接把自定义属性对象写到类的 defaultProps 属性和propTypes 属性
2. 如果使用 class 关键字创建组件，你可以通过在 constructor 中给 this.state 赋值的方式来定义组件的初始状态
3. 对于使用 class 关键字创建的 React 组件，组件中的方法是不会自动绑定 this 的，需要constructor 中为方法手动添加 .bind(this)

#### Fragments

1. Fragments 可以聚合一个子元素列表，并且不在DOM中增加额外节点
2. <></> 是<React.Fragment />的语法糖
3. 带 key 的 Fragments直接使用 <React.Fragment /> ，<></> 语法不能接受键值或属性

- **PS:key 是唯一可以传递给 Fragment 的属性**

#### Portals

1. Portals 提供了一种很好的将子节点渲染到父组件以外的 DOM 节点的方式

```javascript
ReactDOM.createPortal(child, container);
1. child:任何可渲染的 React 子元素,例如一个元素，字符串或碎片
2. container:则是一个 DOM 元素.
```

2. 通过 Portals 进行事件冒泡

#### 错误边界

1. 错误边界：错误边界是用于捕获其子组件树 JavaScript 异常，记录错误并展示一个回退的 UI 的 React 组件，而不是整个组件树的异常
2. 错误边界无法捕获如下错误:
- 事件处理 
- 异步代码 （例如 setTimeout 或 requestAnimationFrame 回调函数）
- 服务端渲染
- 错误边界自身抛出来的错误 （而不是其子组件）

#### 其他点：

1. 只要存在`constructor`就要调用`super(props)`，但是并不是所有的组件都需要constructor的，只有在constructor中使用this.props时才需要使用。