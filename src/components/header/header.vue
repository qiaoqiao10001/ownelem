<template>
  <div class="header">
    <div class="content-wrapper">
      <div class="avatar">
        <img width="64" height="64" :src="seller.avatar" alt="">
      </div>
      <div class="content">
        <div class="title">
          <div class="brand"></div>
          <div class="name">{{seller.name}}</div>
          <div class="deliver">{{seller.description}}/{{seller.deliveryTime}}分钟送达</div>
          <div class="supports">
            <div class="icon" :class="classMap[seller.supports[0].type]"></div>
            <div class="text">{{seller.supports[1].description}}</div>
          </div>
        </div>
        <div class="sups" @click="showdetail">
          <span class="nums">{{seller.supports.length}}个</span>
          <em>&gt;</em>
        </div>
      </div>
    </div>
    <div class="bulletin-wrapper" @click="showdetail">
      <span class="icons"></span>
      <span class="bulletins">{{seller.bulletin}}</span>
      <em>&gt;</em>
    </div>
    <div class="background">
      <img width="100%" height="100%" :src="seller.avatar">
    </div>
    <transition name="fade">
      <div class="detail" v-show="detailShow">
        <div class="detail-wrapper clearfix">
          <div class="detail-main">
            <h1 class="name">{{seller.name}}</h1>
            {{seller.bulletin}}

          </div>
        </div>
        <div class="detail-close">X</div>
      </div>
    </transition>

  </div>

</template>

<script>
export default {
  props:{ //接受传递过来的seller值
    seller:{
      type: Object
    }
  },
  data (){
    return{
      detailShow:false
    }
  },
  methods:{
    showdetail(){
      this.detailShow = true;
    }
  },
  created() {
    this.classMap = ['decrease','discount','guarantee','invoice','special']
  }

}
</script>

<style lang="stylus" scoped>
@import "../../common/stylus/mixin.styl";
@import "../../common/stylus/base.styl";
  .fade-enter-active,.fade-leave-active
    transition opacity .5s
  .fade-enter,.fade-leave-to
    opacity 0
.header
  background rgba(7,17,27,.2)
  position relative
  overflow hidden
  .content-wrapper
    padding-top 24px
    padding-left 24px
    padding-bottom 18px
    font-size 0
    color:#fff

    position relative
    .avatar
      display inline-block
      vertical-align top

    .content
      font-size 12px
      display inline-block

      .title
        margin-left 16px
        margin-top 2px

        .brand
          display inline-block
          width 30px
          height 18px
          vertical-align top
          bg-image('brand')
          background-size 30px 18px
          background-repeat no-repeats
        .name
          display inline-block
          font-size 16px
          font-weight bold
          line-height 18px
        .deliver
          margin-top 8px
          margin-bottom 10px
        .supports
          .text
            display inline
            font-size 10px
          .icon
            display inline-block
            width 12px
            height 12px
            margin-right 4px
            background-size 12px 12px
            background-repeat no-repeat
            vertical-align top
            &.decrease
              bg-image('decrease_1')
            &.discount
              bg-image('discount_1')
             &.guarantee
              bg-image('guarantee_1')
            &.invoice
              bg-image('invoice_1')
             &.special
              bg-image('special_1')
      .sups
        position absolute
        top 40px
        right 24px
        background rgba(0,0,0,.2)
        height 24px
        line-height 24px
        padding 7px 8px 7px 8px
        border-radius 12px
        color #ffffff
        em
          font-style normal
  .bulletin-wrapper
    height 28px
    color #fff
    width 100%
    background-color rgba(7,17,27,.2)
    line-height 28px
    white-space nowrap
    overflow hidden
    text-overflow ellipsis
    font-size 12px
    // padding-left 12px
    // padding-right 22px
    // display flex
    padding-right 22px
    .bulletins
      vertical-align middle
      padding-right 12px
    .icons
      display inline-block
      vertical-align middle
      width 22px
      height 12px
      bg-image('bulletin')
      background-size 22px 12px
      background-repeat no-repeat
      margin-right 4px
      margin-left 12px
  .background
    position absolute
    top 0
    left 0
    width 100%
    height 100%
    z-index -1
    filter blur(10px)
  .detail
    position fixed
    color #fff
    width 100%
    height 100%
    top 0
    left 0
    background rgba(7,17,27,.8)
    z-index 100
    .detail-wrapper
      min-height 100%
      width 100%
      .detail-main
        margin-top 64px
        padding-bottom 64px
        .name
          font-size 16px
          font-weight 700
          line-height 16px
          text-align center

    .detail-close
      position relative
      width 32px
      height 32px
      margin -64px auto 0 auto
      clear both
      font-size 32px
      color #fff


</style>
