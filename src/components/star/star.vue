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

</style>
