## 类和接口

----

### 类实现接口


实现(implements)是面向对象的一个中欧给你要概念.一个类只能继承另外一个类,有时候不同类之间有一些共有的特性,这时候就可以把特性提取成接口(interfaces), 用implements 关键字来实现. 这个特性大大提高了面向对象的灵活性.

防盗门和车都有报警器
```
interface Alarm {
  alert(): void;
}

class Door {

}
class SecurityDoor extends Door implements Alarm {
  alert() {
    console.log('SecurityDoor alert');
  }
}
class Car implements Alarm {
  alert() {
    console.log('car alert');
  }
}
```

一个类可以实现多个接口:

Car实现了Alarm和light接口
```
interface Alarm {
  alert(): void;
}
interface Light {
  lightOn(): void;
  lightOff(): void;
}

class Car implements Alarm, Light {
  alert() {
    console.log('Car alert');
  }
  lightOn() {
    console.log('Car light on');
  }
  lightOff() {
    console.log('Car light off');
  }
}

```

### 接口继承接口


```
interface Alarm {
  alert(): void;
}
interface LightableAlarm extends Alarm {
  lightOn(): void;
  lightOff(): void;
}

```

### 接口继承类

常见面向对象语言中,接口是不能继承类的,但是在TS中却可以.

```
class Point {
  x: number;
  y: number;
  constructor(x: number, y:number) {
    this.x = x;
    this.y = y;
  }
}

interface Point3d extends Point {
  z: number;
}

let point3d: Point3d = {x: 1, y: 2, z: 3};
```

为什么 TS 会支持接口继承类呢?
原理: 实际上我们在声明 class Point时, 除了会创建一个名为 Point的类以外,同时也创建了一个名为Point的类型.

所以我们既可以将Point当作类来用,也可以当作一个类型来用.

```
class Point {
  x: number;
  y: number;
  constructor(x: number, y: number) {
    this.x = x;
    this.y = y;
  }
}
interface PointInstanceType {
  x: number;
  y: number;
}
function printPoint(p: PointInstanceType) {
  console.log(p.x,p.y)
}
printPoint(new Point(1,2))
```
> 接口继承类和接口继承接口 没有什么本质的区别



