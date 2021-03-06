# 类
通过关键词 **class** 创建一个类，并且要始终添加一个 **constructor** -构造方法
```javascript
class Car {
  constructor(name, year) {
    this.name = name;
    this.year = year;
  }
}
```
类不是对象，是作为对象的模板通过**new**来创建对象,在创建对象时会自动调用构造方法

构造方法是一种特殊的方法：

    它必须有确切的名称的 “constructor”
    创建新对象时自动执行
    用于初始化对象属性
    如果您没有定义构造方法，JavaScript 会添加一个空的构造方法。
在类中也可以创建类方法。
# 类继承
继承对于代码可重用性很有用：在创建新类时重用现有类的属性和方法。

下面创建一个继承自类“Car”的类Model

```js
class Car {
  constructor(brand) {
    this.carname = brand;
  }
  present() {
    return 'I have a ' + this.carname;
  }
}
class Model extends Car {
  constructor(brand, mod) {
    super(brand);
    this.model = mod;
  }
  show() {
    return this.present() + ', it is a ' + this.model;
  }
}
let myCar = new Model("Ford", "Mustang");
document.getElementById("demo").innerHTML = myCar.show();
```
通过在 **constructor** 方法中调用 **super()** 方法，我们调用了父级的 constructor 方法，获得了**父级的属性和方法**的访问权限。

# Getter和Setter
在最终返回之前可以通过 get 和 set 来获取值并对他们进行一定的操作。
```js
class Car {
  constructor(brand) {
    this._carname = brand;  //用_将实际属性值与Getter和Setter区分开
  }
  get carname() {
    return this._carname;
  }
  set carname(x) {
    this._carname = x;
  }
}
let myCar = new Car("Ford");
myCar.carname = "Volv";
document.getElementById("demo").innerHTML = myCar.carname;
```
# Hoisting
与函数和其他 JavaScript 声明不同，类声明不会被提升。
这意味着必须先声明类，然后才能使用它：
# static方法
static方法只能在类上调用，可以将自己的类对象作为参数调用
```js
class Car {
  constructor(name) {
    this.name = name;
  }
  static hello(x) {
    return "Hello " + x.name;
  }
}
let myCar = new Car("Ford");
document.getElementById("demo").innerHTML = Car.hello(myCar);
```