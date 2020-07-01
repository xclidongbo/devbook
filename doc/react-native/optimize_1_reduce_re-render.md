
## 减少re-render

-----


对于React来说, 减少re-render可以说是效益最高的事情了.

### 1️⃣shouldComponentUpdate

```
class Button extends React.Component {
  shouldComponentUpdate(nextProps, nextState) {
    if (this.props.color !== nextProps.color) {
      return true;
    }
    return false;
  }

  render() {
    return <button color={this.props.color} />;
  }
}
```


### 2️⃣React.memo

`React.memo`是React中引入的新功能,是专门针对函数组件的高阶组件
默认情况下,它和`PureComponent`一样,进行浅比较.

```
const MemoButton = React.memo(function Button(props) {
  return <button color={this.props.color} />;
});

```

如果想和`shouldComponentUpdate`一样,自定义比较过程, `React.memo`还支持传入自定义函数:

```
function Button(props) {
  return <button color={this.props.color} />;
}
function areEqual(prevProps, nextProps) {
  if (prevProps.color !== nextProps.color) {
      return false;
    }
  return true;
}
export default React.memo(MyComponent, areEqual);

```

> 注意:`areEqual()`这个函数的返回值和`shouldComponentUpdate`正好相反,如果props相等, `areEqual()`返回的是`true`, `shouldComponentUpdate`却返回的是`false`

### 3️⃣React.PureComponent

```
class PureComponentButton extends React.PureComponent {
  render() {
    return <button color={this.props.color} />;
  }
}
```

会在组件更新前对props和state做一次浅比较.如果层级过多,比如多层Object,这时候利用`shouldComponentUpdate`来手动管理


社区上其它解决方案:

- 把组件细分成更小的子组件,然后统一用`PureComponent`进行渲染时机的管理.
- 使用`immutable`对象,再配合`PureComponent`进行数据比较

