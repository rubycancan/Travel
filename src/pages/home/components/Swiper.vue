<template>
  <div class="wrapper">
    <swiper :options="swiperOption">
      <!-- slides -->
      <swiper-slide v-for="item of swiperList" :key="item.id">
        <img class="swiper-img" :src="item.imgUrl" />
      </swiper-slide>
      <!-- Optional controls -->
      <div class="swiper-pagination"  slot="pagination"></div>
    </swiper>
  </div>
</template>

<script>
export default {
  name: 'HomeSwiper',
  data () {
    return {
      swiperOption: {
        pagination: '.swiper-pagination',
        loop: true
      },
      swiperList: [{
        id: '0001',
        imgUrl: 'http://mp-piao-admincp.qunarzz.com/mp_piao_admin_mp_piao_admin/admin/20196/cdf8e74f9c7dfb886af145efc69cf6e2.jpg_750x200_4db2ecac.jpg'
      }, {
        id: '0002',
        imgUrl: 'http://mp-piao-admincp.qunarzz.com/mp_piao_admin_mp_piao_admin/admin/20199/0fa39f9f5e66189e85b5c6e54278587d.jpg_750x200_86c8f2d8.jpg'
      }]
    }
  }
}
</script>

<style lang="stylus" scoped>
  .wrapper >>> .swiper-pagination-bullet-active
    background: white
  .wrapper
    overflow: hidden
    width: 100%
    height: 0
    padding-bottom: 26.7%
    background：#ccc
    .swiper-img
      width: 100%
</style>
