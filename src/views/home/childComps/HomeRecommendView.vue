<template>
  <div class="recommend">
    <div v-for="(item,index) in recommends"
         :key="index"
         class="recommend-item">
      <a :href="item.link">
        <img :src="item.image"
             alt="">
        <div>{{item.title}}</div>
      </a>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    recommends: {
      type: Array,
      default () {
        return []
      }
    },
  },
}
</script>

<style scoped>
.recommend {
  display: flex;
  width: 100%;
  text-align: center;
  font-size: 12px;
  padding: 10px 0 30px 0;
  border-bottom: 10px solid #eee;
}
.recommend-item{
  flex: 1;
}
.recommend-item img{
  width: 70px;
  height: 70px;
  margin: 0 0 5px 0;
}
</style>