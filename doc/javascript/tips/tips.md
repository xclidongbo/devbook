## 打印多个对象

```
const foo = {name: 'tom', age: 30, nervous: false};
const bar = {name: 'tom', age: 30, nervous: false};
const baz = {name: 'tom', age: 30, nervous: false};

'Bad Code ❌'

console.log(foo)
console.log(bar)
console.log(baz)

'Good Code ✅'

console.log({foo,bar,baz})
console.tab([foo,bar,baz])
```

## 花费时间

```
console.time('looper')

let i=0;
while (i<10000) {i++}
console.timeEnd('looper')

```

## 堆栈打印log

```
const deleteMe = () => console.trace('bye bye database')
deleteMe()
deleteMe()
```


## 高级tag例子

```
const horse = {
  name: '🐴',
  size: 'large',
  skills: ['jousting','racing'],
  age: 7
}

'Bad Code ❌'
let bio = horse.name + ' is a' + horse.size + 'horse skilled in ' + horse.skills.join(' & ')

'Good Code ✅'
const {name, size, skills} = horse;
bio = `${name} is a ${size} skilled in ${skills.join(' & ')}`

function horseAge(str, age) {
  const ageStr = age > 5 ? 'old': 'young';
  return `${str[0]}${ageStr} at ${age} years`
}
const bio2 = horseAge`This horse is ${horse.age}`;

```



