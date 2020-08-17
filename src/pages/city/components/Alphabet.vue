<template>
  <ul class="list">
    <li class="item" 
        v-for="item of letters" 
        :key="item"
        :ref="item"
        @click="handleLetterClick"
        @touchstart.prevent="handleTouchStart"
        @touchmove="handleTouchMove"
        @touchend="handleTouchend"
    >{{item}}</li>
  </ul>
</template>

<script>
export default {
  name: 'CityAlphabet',
  props : {
    cities : Object
  },
  data () {
    return {
      touchStatus : false,
      startY : 0,
      timer : null
    }
  },
  computed : {
    letters () {
      var letters = []
      for(var prop in this.cities) {
        letters.push(prop)
      }
      return letters
    }
  },
  updated () {  //一开始的cities是空数组，等Ajax请求到数据后，页面重新渲染，updated就会触发
    this.startY = this.$refs['A'][0].offsetTop
  },
  methods : {
    handleLetterClick : function (e) {
      this.$emit('change', e.target.innerText)
    },
    handleTouchStart () {
      this.touchStatus = true
    },
    handleTouchMove (e) {
      if(this.touchStatus) {
        if(this.timer) {
          clearTimeout(this.timer)
        }
        this.timer = setTimeout(() => { //用箭头函数this指向组件
                                        //用function this指向window
          var touchY = e.targetTouches[0].clientY - 79
          var index = Math.floor((touchY - this.startY) / 20)
          if(index >= 0 && index < this.letters.length) {
            this.$emit('change', this.letters[index])
          }
        }, 16)
      }
    },
    handleTouchend () {
      this.touchStatus = false
    }
  }
}
</script>

<style lang="stylus" scoped>
  @import '~styles/varibles.styl'
  .list
    display:flex
    flex-direction:column
    justify-content:center
    position:absolute
    top:1.58rem
    right:0
    bottom:0
    width:.4rem
    .item
      text-align:center
      line-height:.4rem
      color:$bgColor
</style>
