<template>
  <div class="tab-control">
    <div v-for="(item,index) in titles"
         :key="index"
         class="tab-control-item"
         :class="{active:index === currentIndex}"
         @click="itemClick(index)">
      <span>{{item}}</span>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    titles: {
      type: Array,
      default () {
        return []
      }
    },
  },
  data () {
    return {
      currentIndex: 0
    }
  },
  methods: {
    itemClick (index) {
      this.currentIndex = index
      // 子传父
      this.$emit('tabClick',index)
    }
  },

}
</script>

<style scoped>
.tab-control {
  display: flex;
  text-align: center;
  font-size: 15px;
  height: 40px;
  line-height: 40px;
}
span {
  padding: 5px;
}
.tab-control-item {
  flex: 1;
}
.active span {
  color: var(--color-high-text);
  border-bottom: 3px solid var(--color-tint);
}
</style>