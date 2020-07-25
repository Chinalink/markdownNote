# 面向对象的JavaScript

#### 动态语音类型和鸭子类型

编程语言按照数据类型大体可以分为两类，一类是**静态类型语言**，另一类型是**动态类型语言**。JavaScript是一门典型的动态类型语言。

动态类型语言对变量类型的宽容给实际编码带来了很大的灵活性。由于无需进行类型检测，我们可以尝试调用任何对象的任意方法，而无需去考虑它原本是否被设计为拥有该方法。

> 鸭子类型：如果它走起路来像鸭子，叫起来也是鸭子，那么它就是鸭子。

鸭子类型指导我们只关注对象的行为，而不关注对象本身，也就是关注HAS-A，而不是IS-A。

```javascript
var duck = {
  duckSinging: function() {
    console.log(`嘎嘎嘎`);
  }
}

var chicken = {
  duckSinging: function() {
    console.log(`嘎嘎嘎`);
  }
} 

var choir = [] // 合唱团
var joinChoir = function(animal) {
  if(animal && typeof animal.duckSinging === `function`) {
    choir.push(animal)
    console.log(`恭喜加入合唱团`)
    console.log(`合唱团已有成员数量：${choir.length}`)
  }
}

joinChoir(duck)
joinChoir(chicken)
```



#### 多态

多态的实际含义：同一操作作用于不同的对象上面，可以产生不同的解释和不同的执行结果。换句话说，给不同的对象发送同一个消息的时候，这些对象会根据这个消息分别给出不同的反馈。

```JavaScript
var makeSound = function(animal) {
  if(animal instanceof Duck) {
    console.log(`嘎嘎嘎`);
  } else if (animal instanceof Chicken) {
    console.log(`咯咯咯`);
  }
}

var Duck = new function(){}
var Chicken = new function(){}

makeSound(new Duck()) // 嘎嘎嘎
makeSound(new Chicken()) // 咯咯咯
```

多态背后的思想是将“做什么”和“谁去做以及怎样去做”分离开来，也就是将“不变的事物”与“可能改变的事物”分离开来。把不变的部分隔离出来，把可变的部分封装起来，这给予了我们扩展程序的能力，程序看起来是可生长的，也是符合开发-封闭原则的。

```javascript
var makeSound = function (animal) {
  animal.sound()
}

var Duck = function () {}

Duck.prototype.sound = function () {
  console.log(`嘎嘎嘎`);
}

var Chicken = function () {}

Chicken.prototype.sound = function () {
  console.log(`咯咯咯`);
}

makeSound(new Duck()) // 嘎嘎嘎
makeSound(new Chicken()) // 咯咯咯
```

使用继承来得到多态效果，是让对象表现出多态性的最常用手段。继承通常包括实现继承和接口继承。