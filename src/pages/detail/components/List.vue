<template>
  <div>
    <div
      class="item"
      v-for="(item, index) of ticketList"
      :key="index"
    >
      <div class="item-title border-bottom">
        <span class="item-title-icon"></span>
        {{item.title}}
      </div>
      <div v-if="item.children" class="item-children">
        <detail-list :list="item.children"></detail-list>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'DetailList',
  props: {
    list: {
      type: Array,
      default () {
        return []
      }
    }
  },
  data () {
    return {
      noTicket: [{title: '景点门票尚未上线，敬请期待......'}]
    }
  },
  computed: {
    ticketList () {
      if (this.list.length !== 0) {
        return this.list
      } else {
        return this.noTicket
      }
    }
  }
}
</script>

<style lang="stylus" scoped>
  .item-title
    line-height: .8rem
    font-size: .32rem
    padding: 0 .2rem
    .item-title-icon
      position: relative
      left: .06rem
      top: .06rem
      display: inline-block
      width: .36rem
      height: .36rem
      background: url(https://s.qunarzz.com/piao/image/touch/sight/detail.png)  0 -.45rem no-repeat
      background-size: .4rem 3rem
      margin-right: .1rem
  .item-children
    padding: 0 .1rem
    .item-title
      font-size: .3rem
    .item-title-icon
      display: inline
</style>
