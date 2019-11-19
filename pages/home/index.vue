<template>
  <div class="container">
    <div>
      <h1 class="title">
        我是页面内容
        {{subTitle}}
      </h1>
    </div>
  </div>
</template>
<script>

export default {
  layout: 'home',

  asyncData({ $axios, params }) {
    // 最重要的一个键, 支持异步数据处理，另外该方法的第一个参数为当前页面组件的上下文对象。
    return $axios.get('')
    .then((res) => {
      return { subTitle: res.data.subTitle }
    })
  },
  fetch() {
    // 与 asyncData 方法类似，用于在渲染页面之前获取数据填充应用的状态树（store）。不同的是 fetch 方法不会设置组件的数据。
  },
  head() {
    // 配置当前页面的 Meta 标签, 详情参考 页面头部配置API。
  },
  loading: false, // 如果设置为false，则阻止页面自动调用this.$nuxt.$loading.finish()和this.$nuxt.$loading.start(),您可以手动控制它,请看例子,仅适用于在nuxt.config.js中设置loading的情况下。
  transition: '', // 指定页面切换的过渡动效
  scrollToTop: true, // 布尔值，默认: false。 用于判定渲染页面前是否需要将当前页面滚动至顶部
  validate ({ params }) { // 校验方法用于校验 动态路由的参数。
    return true
  },
  middleware: 'auth', // 指定页面的中间件，中间件会在页面渲染之前被调用，
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 30px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
