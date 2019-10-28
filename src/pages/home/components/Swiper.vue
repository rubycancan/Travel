<template>
  <div class="wrapper" >
      <swiper :options="swiperOption" v-if="showSwiper" ref="mySwiper">
        <!-- slides -->
        <swiper-slide v-for="item of list" :key="item.id">
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
  props: {
    list: Array
  },
  data () {
    return {
      swiperOption: {
        pagination: '.swiper-pagination',
        loop: true,
        autoplay: 5000,
        speed: 3000,
        observeParents: true,
        observer: true
      }
    }
  },
  methods: {
    swiperRefresh () {
      if (this.$refs.mySwiper) {
        const swiper = this.$refs.mySwiper.swiper
        swiper.init()
        swiper.stopAutoplay()
        swiper.startAutoplay()
      }
    }
  },
  computed: {
    showSwiper () {
      return this.list.length
    }
  },
  activated () {
    this.swiperRefresh()
  }
  // 如果不想要报警告和重新渲染，去掉deactivated就可以了，但是轮播效果会失效，因为computed要在数据发生变化的时候才会执行，
  //   也就是说要在prop里的list值传进来之后才会执行，而swiper组件因为缓存的原因已经加载了确得不到list的数据，所以会显示最后
  //   一页和轮播失效，要解决就必须得当数据进来之后再加载swiper组件
  // deactivated () {
  //   this.list = []
  // }
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
