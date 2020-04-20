## 类型推论

---

如果没有明确指明类型,那么TypeScript会依照类型推论的规则推断出一个类型

如:
```
let myFav = 'seven';
<!-- 等价于 -->
let myFav: string = 'seven'
```

如果定义的时候没有赋值, 就是`any`类型而不被类型检查

