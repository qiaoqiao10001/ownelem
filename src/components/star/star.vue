<template>
  <div class="star" :class="starType">
    <span v-for="(index,itemClass) in itemClasses" :class="itemClass" class="star-item" :key="index"></span>
  </div>
</template>

<script>
export default {
  props:{
    size:{
      type:Number
    },
    score:{
      type:Number
    }
  },

}
</script>

<style lang="stylus" scoped>
  .star
    font-size 0 //去除由于元素间隔带来的间距
    .star-item
      display inline-block
      background-repeat no-repeat
    &.star-48
      .star-item
        width 20px
        height 20px
        margin-right 22px
        background-size 20px 20px
        
</style>
