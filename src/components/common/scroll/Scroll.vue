<template>
  <div class="wrapper"
       ref="wrapper">
    <div class="content">
      <slot></slot>
    </div>
  </div>
</template>

<script>
import BScroll from 'better-scroll'

export default {
  props: {
    probeType: {
      type: Number,
      default: 0
    },
    pullUpLoad: {
      type: Boolean,
      default: false
    },
  },
  data () {
    return {
      scroll: null
    }
  },
  mounted () {
    // 1、创建BScroll对象
    this.scroll = new BScroll(this.$refs.wrapper, {
      observeDOM: true,
      click: true,
      probeType: this.probeType,
      pullUpLoad: this.pullUpLoad
    })

    // 2、监听滚动的位置
    if (this.probeType == 3) {
      this.scroll.on('scroll', (position) => {
        // console.log(position);
        this.$emit('scroll', position)
      })
    }

    // 3、监听上拉事件
    if (this.pullUpLoad) {
      this.scroll.on('pullingUp', () => {
        // console.log('1');
        this.$emit('pullingUp')
      })
    }

  },
  methods: {
    // 返回顶部
    scrollTo (x, y, time) {
      this.scroll && this.scroll.scrollTo(x, y, time)
    },
    // 上拉加载
    finishPullUp () {
      this.scroll && this.scroll.finishPullUp()
    },
    // 刷新
    refresh () {
      this.scroll && this.scroll.refresh()
    },
    // 
    getScrollY(){
      return this.scroll ? this.scroll.y : 0
    }
  },
}
</script>

<style scoped>
</style>