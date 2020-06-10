## 声明合并


----


### 函数的合并

之前学过,我们可以使用重载定义多个函数类型
```
function reverse(x: number): number;
function reverse(x: string): string;
function reverse(x: number | string): number: string {
  if (typeof x === 'number') {
        return Number(x.toString().split('').reverse().join(''));
    } else if (typeof x === 'string') {
        return x.split('').reverse().join('');
    }
}
```

### 接口的合并

```
interface Alarm {
  price: number;
}
interface Alarm {
  weight: number;
}


// 相当于:
interface Alarm {
  price: number;
  weight: number;
}

```


> 合并的属性类型必须一致,类型不一致会报错.


### 类的合并

类的合并与接口合并规则一样

