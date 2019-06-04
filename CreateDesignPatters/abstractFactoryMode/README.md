## 抽象工厂模式
  
  通过对类的工厂抽象使其业务用于对产品类簇的创建，而不负责创建某一类产品的实例。

  抽象类是一种声明但不能使用的类。 当你使用时会报错。

### DEMO
```
  function Car () {}
  Car.prototype = {
    constructor: Car,
    getPrice () { return new Error('抽象方法不能调用');},
    getSpeed () { return new Error('抽象方法不能调用');}
  };
```

### 幽灵工厂
  抽象工厂通常是用来作为父类并创建一些子类;
```
  // 创建抽象工厂类
  function AbstractFactory (subType, superType) {
    // 判断抽象工厂中是否有该抽象类
    if (typeOf AbstractFactory[superType] === 'function') {
      // 寄生式继承
      // 创建缓存类
      function F () {}
      // 继承父类的属性和方法
      F.prototype = new AbstractFactory[superType]();
      // 子类原型继承父类
      subType.prototype = new F();
      // 改变子类指向
      subType.prototype.constructor = subType;
    } else {
      return new Error('未创建该抽象类');
    }
  }
  // 创建抽象工厂父类
  AbstractFactory.Car = function () {
    this.type = 'car';
  }

  AbstractFactory.Car.prototype.getPrice = function () { return new Error('抽象方法不能调用'); }

  // 创建子类
  function BWM () {}
  // 继承父类属性与方法
  AbstractFactory(BWM, 'Car');
  // 实现父类抽象方法
  BWM.prototype.getPrice = function () {}
  // 添加自己的方法
  BWM.prototype.getSpeed = function () {}

  // 实例化子类
  const bwm = new BWM();
```