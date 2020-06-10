## 类


---

### ES6
#### 属性和方法


```
class Animal {
  constructor(name) {
    this.name = name;
  }
  sayHi() {
    return `My name is ${this.name}`
  }
}

let a = new Animal('Jack');
a.sayHi();

```


#### 类的继承

```
class Cat extends Animal {
  constructor(name) {
    super(name);
    console.log(this.name)
  }
  sayHi() {
    return 'Meow, ' +super.sayHi();
  }
}
```

#### 存取器

```
class Animal {
  constructor(name) {
    this.name = name;
  }
  get name() {
    return 'Jack';
  }
  set name(value) {
    console.log('setter: ' + value)
  }
}

let a = new Animal('Kitty');
a.name = 'Tom';
console.log(a.name);

```

#### 静态方法

```
class Animal {
  static isAnimal(a) {
    return a instanceof Animal;
  }
}

let a  = new Animal('Jack');
Animal.isAnimal(a);
```

### ES7


#### 实例属性

ES6中实例属性只能通过构造函数`this.xxx`来定义, ES7提案可以直接在类中定义:

```
class Animal {
    name = 'Jack';

    constructor() {
        // ...
    }
}

let a = new Animal();
console.log(a.name); // Jack

```

#### 静态属性

```
class Animal {
    static num = 42;

    constructor() {
        // ...
    }
}

console.log(Animal.num); // 42

```

### TypeScript中类的用法


#### public, private和protected

三种访问修饰符:

- `public`属性或者方法共有,可以在任何地方被访问到;
- `private`属性或者方法私有,不能声明它的类的外部访问;
- `protected`修饰的属性和方法是受保护的,和`private`类似,区别是它在子类中是允许访问的.


```
class Animal {
  public name;
  public constructor(name) {
    this.name = name;
  }
}
let a = new Animal('Jack');
console.log(a.name);
a.name = 'Tom';
console.log(a.name);

```


```

class Animal {
  private name;
  public constructor(name) {
    this.name = name;
  }
}
let a = new Animal('Jack');
console.log(a.name);//报错
a.name = 'Tom';//报错


```

```
class Animal {
  private name;
  public constructor(name) {
    this.name = name;
  }
}
class Cat extends Animal {
  constructor(name) {
    super(name);
    console.log(this.name);//子类也不允许访问私有属性
  }
}


```

```

class Animal {
  protected name;
  public constructor(name) {
    this.name = name;
  }
}
class Cat extends Animal {
  constructor(name) {
    super(name);
    console.log(this.name);
  } 
}

```

#### 参数属性


修饰符和`readonly`可以使用在构造函数参数中

```
class Animal {
  public constructor (public name) {

  }
}

```


#### readonly

```
class Animal {
    readonly name;
    public constructor(name) {
        this.name = name;
    }
}

let a = new Animal('Jack');
console.log(a.name); // Jack
a.name = 'Tom';// 报错
```

#### 抽象类


`abstract`用于定义抽象类和抽象方法

- 抽象类不允许被实例化
- 抽象类中的抽象方法必须被子类实现

##### 抽象类不允许被实例化

```
abstract class Animal {
    public name;
    public constructor(name) {
        this.name = name;
    }
    public abstract sayHi();
}

let a = new Animal('Jack'); //报错
```

##### 抽象类中的抽象方法必须被子类实现

```
abstract class Animal {
    public name;
    public constructor(name) {
        this.name = name;
    }
    public abstract sayHi();
}

class Cat extends Animal {
    public eat() {
        console.log(`${this.name} is eating.`);
    }
}

let cat = new Cat('Tom');
// 因为没有实现抽象方法sayHi所以编译报错.
```

#### 类的类型

```
class Animal {
  name: string;
  constructor(name: string) {
    this.name = name;
  }
  sayHi():string {
    return 'My name is ${this.name}';
  }
}
let a: Animal = new Animal('Jack');

```

