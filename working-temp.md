### 序列化api的request及response
* 先調整cc, 只回value不組欄位
* 透過1u條列出目前的request及response
* orderform的response會有那些欄位?
```js
class MyClass {
  constructor(name, age, sex) {
    this.name = name,
    this.age = age,
    this.sex = sex
  }
}

var myClass = new MyClass("judy", 28, "female")

console.log(JSON.stringify(myClass));
```
結果: 
```json
{
    "name": "judy",
    "age": 28,
    "sex": "female"
}
```

---
