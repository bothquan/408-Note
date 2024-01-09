# catalog
- [catalog](#catalog)
- [v-if](#v-if)
- [循环](#循环)

# v-if
```js
<tag v-if="isTure"></tag>


new Vue({
    el:....,
    data:{
        isTrue: ture//当为true是上面的tag标签存在，否则不显示
    }
})
```

# 循环
```html
div id = "app">
    <ol>
        <li v-for ="todo in todos"><!--这句有点想for(i : arr)-->
            {{todo.text}}<!--一般的绑定-->>
        </li>
    </ol>
</div>
    <script>
        new Vue({
            el: "#app",
            data:{
                todos: [<!--todos是一个数组，里面是json-->
                    {text: "math"},
                    {text: "english"},
                    {text: "chiese"}
                ]    
            }
        })
    </script>
```
