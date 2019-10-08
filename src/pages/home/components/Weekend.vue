<template>
  <div>
    <div class="recommend-title">周末去哪儿</div>
    <ul>
      <li class="item border-bottom" v-for="item of recommendList" :key="item.id">
        <div class="item-img-wrapper">
        <img alt="" class="item-img" :src="item.imgUrl" />
        </div>
        <div class="item-info">
          <p class="item-title">{{item.title}}</p>
          <p class="item-desc">{{item.desc}}</p>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HomeWeekend',
  data () {
    return {
      recommendList: [{
        id: '0001',
        imgUrl: 'https://imgs.qunarzz.com/sight/source/1505/51/e2ca4d053e34af.jpg_r_640x214_8e7cfb53.jpg',
        title: '爱上大自然',
        desc: '这个周末不想出远门,就在美丽的南宁周边放风吧，让你玩个不停乐个不够'
      }, {
        id: '0002',
        imgUrl: 'https://imgs.qunarzz.com/sight/source/1505/91/8bb1616704e022.jpg_r_640x214_609800b7.jpg',
        title: '南宁必打卡',
        desc: '青山塔影、南湖情韵、邕江春泛'
      }, {
        id: '0003',
        imgUrl: 'https://imgs.qunarzz.com/sight/source/1509/b0/83481d0d95a39b.jpg_r_640x214_7dc3d605.jpg',
        title: '秘境广西',
        desc: '想知道真实的桂林之景和作者笔下的桂林有差别吗？快来揭晓你心中那个未知之谜吧'
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
  .item-img-wrapper
    width: 100%
    overflow: hidden
    height: 0
    padding-bottom: 33.9%
    .item-img
      width: 100%
  .item-info
    padding: .1rem
    .item-title
      line-height: .54rem
      font-size: .32rem
      ellipsis()
    .item-desc
      line-height: .4rem
      color: #ccc
      ellipsis()
</style>
