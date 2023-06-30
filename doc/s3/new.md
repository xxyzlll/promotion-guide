## `new` 关键字的作用

使用 `new` 关键字有以下几个作用：

1. 创建一个空对象。
2. 将这个空对象的原型指向构造函数的原型对象。
3. 执行构造函数，将构造函数中的 `this` 绑定到新创建的对象上。
4. 如果构造函数没有显式返回一个对象，则返回新创建的对象。

## 示例

让我们通过一个示例来说明 `new` 的使用。

```javascript
// 构造函数
function Person(name, age) {
  this.name = name;
  this.age = age;
}

// 使用 new 关键字创建对象实例
const person1 = new Person("Alice", 25);
console.log(person1.name); // 输出 "Alice"
console.log(person1.age); // 输出 25

const person2 = new Person("Bob", 30);
console.log(person2.name); // 输出 "Bob"
console.log(person2.age); // 输出 30
```

在上面的示例中，我们定义了一个 `Person` 构造函数，它接受两个参数 `name` 和 `age`。当我们使用 `new` 关键字调用 `Person` 构造函数时，会创建一个新的对象实例。这个新对象会拥有 `name` 和 `age` 属性，这些属性是通过构造函数的 `this` 关键字来添加的。

值得注意的是，构造函数内部没有显式返回任何对象。根据 `new` 的工作原理，新创建的对象将会作为 `new` 表达式的结果返回。

## 原型链

在使用 `new` 关键字时，新创建的对象实例会继承构造函数的原型对象上的属性和方法。这意味着，通过原型链，我们可以在对象实例上访问构造函数原型对象上的方法和属性。

```javascript
// 构造函数
function Person(name, age) {
  this.name = name;
  this.age = age;
}

// 构造函数原型上的方法
Person.prototype.introduce = function() {
  console.log(`My name is ${this.name} and I am ${this.age} years old.`);
};

// 使用 new 关键字创建对象实例
const person = new Person("Alice", 25);
person.introduce(); // 输出 "My name is Alice and I am 25 years old."
```

在上面的示例中，我们给 `Person` 构造函数的原型对象添加了一个 `introduce` 方法。通过 `new` 创建的 `person` 对象实例可以访问并调用这个方法。

## `new` 的注意事项

在使用 `new` 过程中，有一些需要注意的事项：

1. 构造函数的名称通常以大写字母开头，以便与普通函数区分。
2. 如果构造函数具有参数，我们可以在 `new` 关键字后面传入这些参数。
3. 如果我们忘记使用 `new` 关键字，构造函数将会以普通函数形式执行，并且 `this` 将会绑定到全局对象（在浏览器中是 `window` 对象）上，而不会创建新的对象实例。
4. 使用 `new` 关键字创建对象实例时，可以省略参数括号，比如 `const person = new Person;`，但这种写法容易引起混淆，因此建议始终使用 `()` 来表示无参数。