## 工厂方法模式

  工厂方法模式: 通过对产品类的抽象使其创建业务主要负责用于创建多类产品的实例。 (即: 抽象产品类，然后根据其传入的产品类型创建相应的产品类的实例;)

### 安全模式类
```
  const Demo = function () {
    if (!(this instanceof Demo)) {
      return new Demo();
    }
    this.name = 'srbtj';
    this.age = 18;
  }

  Demo.prototype.showName = function () {
    console.log(this.name);
  }
  Demo.prototype.showAge = function () {
    console.log(this.age);
  }
  var d = Demo();
  d.showName();
  d.showAge();
```

### 安全工厂方法
```
const Factory = function (type, content) {
  if (this instanceof Factory) {
    return new this[type](content);
  } else {
    return new Factory(type, content);
  }
}

Factory.prototype = {
  constructor: Factory,
  'Javascript': function (content) {
    this.content = content;
    console.log(this.content);
  },
  'Php': function (content) {
    this.content = content;
    console.log(this.content);
  },
  'Nodejs': function (content) {
    this.content = content;
    console.log(this.content);
  }
}

Factory('Javascript', 'javascript是世界上最好的语言');
```