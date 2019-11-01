<template>
  <div>
    <div class="banner" @click="handleBannerClick">
      <img class="banner-img" alt="" :src="showBanner" />
      <div class="banner-info">
        <div class="banner-title">
         {{this.sightName}}
        </div>
        <div class="banner-number">
          <span class="iconfont banner-icon">&#xe692;</span>
         {{this.length}}
        </div>
      </div>
    </div>
    <fade-animation>
      <common-gallary
        :imgs="bannerImgs"
        v-show="showGallery"
        @close="handleGalleryClose"
      ></common-gallary>
    </fade-animation>
  </div>
</template>

<script>
import picture from '../../../assets/images/no-picture.png'
import CommonGallary from 'common/gallery/Gallery'
import FadeAnimation from '../../../common/fade/FadeAnimation'
export default {
  name: 'DetailBanner',
  props: {
    sightName: String,
    bannerImg: String,
    bannerImgs: Array
  },
  data () {
    return {
      showGallery: false,
      // imgs: ['http://img1.qunarzz.com/sight/p0/201212/24/711e05d23489891893835fbb.png_r_800x800_0222ecaa.png',
      //   'http://img1.qunarzz.com/sight/p0/1412/4b/1f55d0cff9b73c1dfcf5593032d44b0d.water.jpg_r_800x800_ff3f3c6b.jpg',
      //   'http://img1.qunarzz.com/sight/p0/201212/24/583f44054b12278693835fbb.png_r_800x800_54fb1cb4.png']
      showBanner: this.bannerImg
    }
  },
  computed: {
    length () {
      if (this.bannerImgs) {
        return this.bannerImgs.length
      } else {
        return 0
      }
    },
    banner () {
      if (this.bannerImg) {
        return this.bannerImg
      } else {
        return picture
      }
    }
  },
  methods: {
    handleBannerClick () {
      this.showGallery = true
    },
    handleGalleryClose () {
      this.showGallery = false
    },
    getBanner () {
      setTimeout(() => {
        this.showBanner = this.banner
      }, 300)
      setTimeout(() => {
        if (this.showBanner !== this.banner) {
          this.showBanner = this.banner
        }
      }, 800)
    }
  },
  components: {
    CommonGallary,
    FadeAnimation
  },
  mounted () {
    this.getBanner()
  }
}
</script>

<style lang="stylus" scoped>
  .banner
    position: relative
    overflow: hidden
    height: 0
    padding-bottom: 55%
    background-color: black
    .banner-img
      width: 100%
    .banner-info
      display: flex
      position: absolute
      left: 0
      right: 0
      bottom: 0
      line-height: .6rem
      background-image: linear-gradient(top, rgba(0, 0, 0, 0), rgba(0, 0, 0, 1))
      .banner-title
        flex: 1
        color: white
        font-size: .32rem
        padding: 0 .2rem
      .banner-number
        padding: 0 .4rem
        line-height: .34rem
        height: .34rem
        margin-top: .14rem
        border-radius: .2rem
        background: rgba(0, 0, 0, .8)
        color: white
        font-size: .24rem
      .banner-icon
        font-size: .24rem
</style>
