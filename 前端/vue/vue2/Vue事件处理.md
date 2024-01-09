# catalog
- [catalog](#catalog)
- [v-bind 单项绑定](#v-bind-单项绑定)
- [V-on事件处理](#v-on事件处理)
- [v-model实现双向绑定](#v-model实现双向绑定)


# v-bind 单项绑定
标签内部绑定事件
```html
<p v-bind:text="name"></p>
new Vue({
    el:"",
    data:{
        name: "#"
    }
})
<!-- 可以用:代替v-bind: 式子用js表达式 -->
```
只能是data里面赋值到标签中

# V-on事件处理
```html
  <div id="app">
        <p v-on:click="hiddenMessage" v-if="istrue1">{{message}}</p>
    </div>
  <script>
    var app = new Vue({
        el: "#app",
        data:{
            message: "消息",
            istrue1: "true"
        },
        methods:{
            hiddenMessage: function() {
                app.istrue1 = !app.istrue1;
            }
        }
    })
  </script>  
```
上面对吧传统的js事件，click是函数，但是这里就一个字符串但是有v-on，然后映射到methods对于事件


# v-model实现双向绑定
被绑定放或者绑定方变化都会使另一边变化

```html
    <select v-model="selectone">
        <option value="A被选">A</option>
        <option value="B被选">B</option>
    </select>
    <p>{{selectone}}</p>
    <script>
    var app = new Vue({
        el: "#app",
        data:{
            selectone:''
        }
    })
    </script>
```

v-model只能在表单类元素进行绑定，如`<input>、<textarea> 及 <select>` 

