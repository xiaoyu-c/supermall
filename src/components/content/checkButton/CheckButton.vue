<template>
  <div class="check-button" :class="{check:isChecked}">
    <img src="../../../assets/img/cart/tick.svg" alt="">
  </div>
</template>

<script>
export default {
props: {
  isChecked: {
    type: Boolean,
    default: false
  },
},
}
</script>

<style scoped>
.check-button{
  border-radius: 50%;
  box-shadow: 0 0 5px rgba(0, 0, 0, 0.3);
}
.check{
  background-color: red;
}
</style>