<template>
  <div>
    <div class="recommend-title">热销推荐</div>
    <ul>
      <li class="item border-bottom" v-for="item of recommendList" :key="item.id">
          <img alt="" class="item-img" :src="item.imgUrl" />
        <div class="item-info">
          <p class="item-title">{{item.title}}</p>
          <p class="item-desc">{{item.desc}}</p>
          <button class="item-button">查看详情</button>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HomeRecommend',
  data () {
    return {
      recommendList: [{
        id: '0001',
        imgUrl: 'https://imgs.qunarzz.com/sight/p0/201212/24/711e05d23489891893835fbb.png_200x200_cc12b84a.png',
        title: '南宁海底世界',
        desc: '不一样的地方，不一样的海底世界'
      }, {
        id: '0002',
        imgUrl: 'https://imgs.qunarzz.com/sight/p0/201403/24/b42f530cfe4d87053d35d18c4bc1bd04.jpg_200x200_a7ecf6b4.jpg',
        title: '地王云顶',
        desc: '西南著名高楼，特色透明玻璃走廊'
      }, {
        id: '0003',
        imgUrl: 'https://imgs.qunarzz.com/sight/p0/201403/12/dbbfc37ee2d2a95c5a2cebd66e9676f0.jpg_200x200_250fb50f.jpg',
        title: '杨美古镇',
        desc: '古镇、老街、碧水、金滩、怪树著称'
      }]
    }
  }
}
</script>

<style lang="stylus" scoped>
  @import '~styles/mixins.styl'
  .recommend-title
    margin-top: .2rem
    line-height: .8rem
    background: #eee
    text-indent: .2rem
  .item
    overflow: hidden
    display: flex
    height: 1.9rem
    .item-img
      width: 1.7rem
      height: 1.7rem
      padding: .1rem
    .item-info
      flex: 1
      padding: .1rem
      min-width: 0
      .item-title
        line-height: .54rem
        font-size: .32rem
        ellipsis()
      .item-desc
        line-height: .4rem
        color: #ccc
        ellipsis()
      .item-button
        lign-height: .44rem
        margin-top: .16rem
        background: #ff9300
        padding: .05rem
        border-radius: .06rem
        color: #fff
</style>
