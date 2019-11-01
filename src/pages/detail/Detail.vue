<template>
  <div>
    <detail-banner
      :sightName="sightName"
      :bannerImg="bannerImg"
      :bannerImgs="galleryImgs"
    ></detail-banner>
    <detail-header></detail-header>
    <div class="content">
      <detail-list :list="list"></detail-list>
    </div>
  </div>
</template>

<script>
import DetailBanner from './components/Banner'
import DetailHeader from './components/Header'
import DetailList from './components/List'
import axios from 'axios'
export default {
  name: 'Detail',
  components: {
    DetailBanner,
    DetailHeader,
    DetailList
  },
  data () {
    return {
      sightName: '',
      bannerImg: '',
      galleryImgs: [],
      list: []
      //     [{
      //   title: '去哪儿推荐',
      //   children: [{
      //     title: '南宁海底世界成人票'
      //   }, {
      //     title: '南宁海底世界学生票'
      //   }, {
      //     title: '南宁海底世界老人票'
      //   }]
      // }, {
      //   title: '门票',
      //   children: [{
      //     title: '南宁海底世界成人票'
      //   }, {
      //     title: '南宁海底世界学生票（儿童票）'
      //   }, {
      //     title: '南宁海底世界老人票'
      //   }, {
      //     title: '南宁海底世界门票亲子票（1大1小）'
      //   }]
      // }, {
      //   title: '一日游',
      //   children: [{
      //     title: '【南宁出发】南宁动物园+南宁凤凰山+南宁人民公园+南宁海底世界'
      //   }]
      // }]
    }
  },
  methods: {
    getDetailInfo () {
      axios.get('/api/detail.php', {
        params: {
          detail_id: this.$route.params.id
        }
      }).then(this.handleGetDataSucc)
    },
    handleGetDataSucc (res) {
      res = res.data
      if (res.ret && res.data) {
        const data = res.data
        this.sightName = data.sightName
        this.bannerImg = data.bannerImg
        this.galleryImgs = data.galleryImgs
        this.list = data.categoryList
      }
    }
  },
  mounted () {
    this.getDetailInfo()
  }
}
</script>

<style lang="stylus" scoped>
  .content
   margin-bottom: 1rem
</style>
