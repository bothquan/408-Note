# catalog
- [catalog](#catalog)
- [引入vue.js](#引入vuejs)
- [条件](#条件)
  - [点击事件](#点击事件)


# 引入vue.js
```html
<script src="https://cdn.jsdelivr.net/npm/vue@2/dist/vue.js"></script>

<!--当然还有脚手架，后面-->

<script type = "text/javascript">
    var app = new Vue({
        el: "#app",<!--元素选择，和getelementby什么差不多-->
        data: {
            message: 'hello world'
        }
    })
</script>

```


# 条件
```html
    <div id ="app">
    <p v-if="is">if is ture</p>
    </div>
<script type="text/javascript"> 
    var app = new Vue({
        el: "#app",
        data:{
            // 为false就不显示
            is: false
        }
    });
</script>
```


## 点击事件
