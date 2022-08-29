<template>
  <div class="main-info">
    <div class="main-info-tip">iframe集成测试</div>
    <iframe
      ref="iframe"
      id="iframe"
      frameborder="0"
      :src="iframeSrc"
      style="min-height: 800px;width: 100%"
    >
    </iframe>
  </div>
</template>

<script>

export default {
  // 定义数据
  data () {
    return {
      iframeSrc: '',
      iframe: ''
    }
  },
  created () {
    console.log('-------created--------')
    this.iframeSrc = 'http://10.1.66.56:8081/'
    // this.iframeSrc = 'http://183.238.225.53:8081/'
    // 监听收到消息
    window.addEventListener('message', this.handleMessageEvent)
  },
  methods: {
    handleMessageEvent (event) {
      // console.log('event:' + event.data)
      if (event.data) {
        const data = event.data
        console.log('-------已收到消息', data)
      }
    }
  },
  destroyed () {
    window.removeEventListener('message', this.handleMessageEvent)
  }
}
</script>

<style>
  .home {
    display: flex;
    align-items: center;
    background-color: orange;
    justify-content: center;
  }
  .main-info-tip {
    font-size: 22px;
    background-color: orange;
    text-align: center;
    color: red;
  }
</style>
