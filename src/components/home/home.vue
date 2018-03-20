<template>
<div id="app">
    <div class="header">
      <Heador :seller="seller"></Heador>
    </div>
    <div class="tab border-1px">
      <div class="tab-item">
        <router-link to='/goods'>
          商品
        </router-link>
      </div>
      <div class="tab-item">
        <router-link to="/ratings">
          评论
        </router-link>
      </div>
      <div class="tab-item">
        <router-link to="/seller">
          商家
        </router-link>
      </div>
    </div>
    <div class="content">
      <router-view></router-view>
    </div>


  </div>
</template>

<script>
import Heador from "../header/header"
import Goods from "../goods/goods"
import Ratings from "../ratings/ratings"
import Seller from "../seller/seller"
import axios from 'axios'

const ERR_OK = 0;
export default {
  components:{
    Heador,
    Goods,
    Ratings,
    Seller
  },
  data(){
    return{
      seller:{}
    }
  },
  created(){
    axios.get('/api/seller').then((res) => {
      this.seller = res.data.data;
      console.log(this.seller);
    })

  }

}
</script>

<style lang="stylus" scoped>
@import "../../common/stylus/mixin.styl"
@import "../../common/stylus/base.styl"
@import "../../common/stylus/mixin.styl";
.tab
  display flex
  height 40px
  width 100%
  text-align center
  line-height 40px
  border-1px(rgba(7,17,27,0.1))
  .tab-item
    flex 1
</style>
