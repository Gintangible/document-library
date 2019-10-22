# 页面组成

> index.vue

```
<template>
  <div></div>
</template>

<script>
export default {
    data () {
        return {
        };
    },
    // 没有用到的时候删除掉，不然vue-cli3 会报错
    // mounted() {},
    components: {},
    computed: {},
    methods: {}
}

</script>

//  scoped 需慎用，此会将样式私有化。如果需要改变一些引入的插件样式，需要去掉。
<style lang='scss' scoped>
</style>
```

[style 中使用 scoped](https://segmentfault.com/a/1190000012184604?utm_source=tuicool&utm_medium=referral)

