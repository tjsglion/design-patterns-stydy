## 简单工厂模式

  简单工厂模式又叫静态工厂方法， 由一个工厂对象决定创建某一种产品对象类的实例。 主要是用来创建同一类对象。

### 实现方式

  1、 通过类实例化对象创建

  2、 通过创建一个新对象然后包装增加其属性和功能来实现

  二者的差异: 通过类实例化对象创建工厂模式， 如果这些类继承同一个父类， 那么父类原型上的方法是共用的。 而后一种方法创建的对象都是一个新个体， 所以他们的方法就不能共用。

### 代码

  1、类实例化对象 (对不同的类实例化)

  ```
  // 篮球类
  function Basketball () {
    this.intro = ''; // 介绍信息
  }
  Basketball.prototype.getMember = function () { console.log('5人'); }
  // 足球类
  function Football () {
    this.intro = '';
  }
  Football.prototype.getMember = function () { console.log('11人');}
  const maps = {
    'basketball': new Basketball(),
    'football': new Football()
  };
  // 运动工厂函数
  function SportFactory (type) {
    return maps[type];
  }
  ```

  2、 新对象包装属性 (创建相似对象: 如不同类型的弹框， 书类等)
  ```
  function CreateBook (name, time, type) {
    const obj = new Object();
    obj.name = name;
    obj.time = time;
    obj.type = type;
    obj.getName = function () {};
    return obj;
  }

  const popMaps = {
    'alert': function () {},
    'prompt': function () {},
    'confirm': function () {}
  };
  // 弹框
  function PopFunction (type, content) {
    const obj = new Object();
    obj.content = content;
    obj.show = function () {};
    popMaps[type]();
    return obj;
  }
  ```
