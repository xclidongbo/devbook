## 字符串字面量类型

---

### Demo

```
type EventNames = 'click' | 'scroll' | 'mousemove';

function handleEvent(ele: Element, event: EventNames) {
  // do something
}

handleEvent(document.getElementById('hello'),'scroll');

```

`type`定义了一个字符串字面量类型`EventNames`,它只能取三种字符串的一种.

> 类型别名和字符差un字面量类型都是使用`type`定义


