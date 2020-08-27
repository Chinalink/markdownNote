# 闭包

当函数可以记住并访问所在的词法作用域时，就产生了闭包。即使函数是在当前词法作用域之外执行。

```javascript
function foo() {
  var a = 2;
  function bar () {
    console.log(a) // 2
  }
  bar()
}
foo()
```

bar()对a的引用的方法是词法作用域的查找规则，而这些规则只是**闭包**的一部分。