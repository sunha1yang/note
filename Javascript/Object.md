## Object对象：

### Object 对象的静态方法
#### Object.keys()和Object.getOwnPropertyNames()
1. 作用：遍历对象的属性
2. 参数：一个对象
3. 返回值：一个数组，该数组的成员都是对象自身的（而不是继承的）所有属性名
4. 二者区别：Object.keys方法只返回可枚举的属性，Object.getOwnPropertyNames方法还返回不可枚举的属性名。

**PS**：可枚举性
