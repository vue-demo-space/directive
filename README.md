# 自定义指令

有的情况下，你仍然需要 **对普通 DOM 元素进行底层操作**，这时就会用到自定义指令

比如，指定一个页面加载时就聚焦的输入框：

```vue
<template>
  <input v-focus/>
</template>

<script>
export default {
  directives: {
    focus: {
      // 当被绑定的元素插入到 DOM 时
      inserted (el) {
        // 这里可以进行 dom 操作
        el.focus()
      }
    }
  }
}
</script>
```

也可以全局注册：

```js
// 注册一个全局自定义指令 `v-focus`
Vue.directive('focus', {
  // 当被绑定的元素插入到 DOM 中时……
  inserted: function (el) {
    // 聚焦元素
    el.focus()
  }
})
```

* [钩子函数](https://cn.vuejs.org/v2/guide/custom-directive.html#%E9%92%A9%E5%AD%90%E5%87%BD%E6%95%B0)
* [钩子函数参数](https://cn.vuejs.org/v2/guide/custom-directive.html#%E9%92%A9%E5%AD%90%E5%87%BD%E6%95%B0%E5%8F%82%E6%95%B0)

很多时候，你可能想在 `bind` 和 `update` 时触发相同行为，而不关心其他钩子，可以这样简写：

```js
Vue.directive('color-swatch', function (el, binding) {
  el.style.backgroundColor = binding.value
})
```

demo 注册了 v-highlightjs 指令用 highlightjs 来渲染代码块