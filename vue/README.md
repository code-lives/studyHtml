# Vue [文档](https://v3.cn.vuejs.org/api/)
#### 初始化
绑定赋值
````html
<div id="app">
    {{ message }}= Hello Vue!
</div>
````
````javascript
var app = new Vue({
    el: '#app',
    data: {
        message: 'Hello Vue!'
    }
})
````
#### computed
计算属性 优雅的计算 不需要在html 里面计算
````html
<div id="app">
    {{ Numsum }} = 3
</div>
````
````javascript
var app = new Vue({
    el: '#app',
    data: {
        message: 'Hello Vue!',
        age:1,
        num:2,
    },
    computed:{
        Numsum(){
            return this.age+num;
        }
    },
})
````
#### methods
添加点击事件 计算属性
````html
<div id="app">
    {{ Numsum }} = 3
</div>
````
````javascript
var app = new Vue({
    el: '#app',
    data: {
        message: 'Hello Vue!',
        age:1,
        num:2,
    },
    methods:{
        Numsum(){
            return this.age+num;
        }
    },
})
````

#### watch
监控值的变化,进行其他操作
````html
<div id="app">
    <button @click="Onclick">Click</button>
</div>
````
````javascript
var app = new Vue({
    el: "#app",
    data: {
        age: 1,
        num: 2,
        contents: {
            "age": 1,
            "name": "张三"
        }
    },
    computed: {
        Numsum() {
            return this.age + this.num
        }
    },
    methods: {
        Onclick() {
            this.age++
        }
    },
    watch: {
        //改变值时候出发
        age(newval, lodval) {
            console.log("新的：" + newval + "，旧的：" + lodval);
        },
        //初始化触发
        num: {
            handler(newval, lodval) {
                console.log("新的：" + newval + "，旧的：" + lodval);
            },
            immediate: true,
        },
        //针对数组内 任意变化
        contents: {
            handler(newval, lodval) {
                console.log("新的：" + newval + "，旧的：" + lodval);
            },
            deep: true,
        },
        //针对数组内单个值
        "contents.age" (newval, lodval) {
            console.log("新的：" + newval + "，旧的：" + lodval);
        }
    }
})
````
#### if else if
判断 注释("<!->")
````html
<div id="app">
    <div v-if="age ==1">1</div>
    <div v-else-if="age == 2">2</div>
    <div v-else=>120</div>
</div>
````
````javascript
var app = new Vue({
el: "#app",
data: {
    age: 1,
})
````
#### is-show
显示和隐藏（display:none）
````html
<div id="app">
    <div v-isshow="IsShow">1</div>
</div>
````
````javascript
var app = new Vue({
el: "#app",
data: {
    IsShow: true, //布尔值
})
````
#### v-for
便利数组
````html
 <div id="app">
    <ul>
        <li v-for="user in users">{{user.age}}-{{user.name}}</li>
        <li v-for="(val,key,index) in users">{{index}}-{{key}}-{{val.age}}-{{val.name}}</li>
    </ul>
</div>
````
````javascript
var app = new Vue({
    el: "#app",
    data: {
        users: [{
            "age": 18,
            "name": "张三",
        }, {
            "age": 19,
            "name": "李四",
        }, {
            "age": 20,
            "name": "王五",
        }, ],
    },
})
````
#### v-model
输入的值和页面的值一起动，类似于手机预览模式（手机模型上面的值跟着一起变）
````html
<div id="app">
        {{age}}
        <input type="text" v-model="age">
</div>
````
````javascript
var app = new Vue({
    el: "#app",
    data: {
        age: 10
    },
})
````