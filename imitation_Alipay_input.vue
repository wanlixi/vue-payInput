<template>
  <div class="alipay">
     <ul class="pwd" @click="blurInput">
	<li
	  v-for="(item, index) in pwds" 
	  :key="index" 
	  :class="['pw', item.isInput ? 'is_inputed' : '']"></li>
     </ul>
     <input class="pwd_input" type="number" v-model="realPwd" maxlength="6">
  </div>
</template>
<script>
export default {
  data () {
    return {
      pwds: [
        {isInput: false},
        {isInput: false},
        {isInput: false},
        {isInput: false},
        {isInput: false},
        {isInput: false},
      ],
      realPwd: ''
    }
  },
  watch: {
    realPwd (realPwd) {
      // realPwd = realPwd.substr(0,6);
      // console.log(realPwd.length)
      this.realPwd.length == 6 && (document.getElementsByClassName('pwd_input')[0].blur())
      for (let i = 0; i < 6; i++) {
      	this.pwds[i].isInput = false;
      }
      for (let i = 0, j = realPwd.length; i < j; i++) {
      	this.pwds[i].isInput = true;
      }
    }
  },
  methods: {
    blurInput () {
      document.getElementsByClassName('pwd_input')[0].focus()
    }
  }
}
</script>
<style lang="stylus" scoped>
$inputLength = 1rem;/* 50px */
$dottedWidth = .2rem;/* 10px */
.alipay
  position relative
  width: ($inputLength * 6)
  height: $inputLength
  margin 300px auto
.pwd, .pwd_input
  position absolute
  top 0
  left 0
.pwd
  display flex
  width ($inputLength * 6)
  height $inputLength
  z-index: 10
.pw
  width $inputLength
  height $inputLength
  line-height $inputLength
  text-align center
  border 1px solid #ddd
  border-right-width 0
  font-size .4rem/* 20px */
  position relative
.is_inputed:before
  content ''
  position absolute
  top (($inputLength - $dottedWidth) / 2)
  left (($inputLength - $dottedWidth) / 2)
  width $dottedWidth
  height $dottedWidth
  border-radius ($dottedWidth / 2)
  background #000
.pw:nth-last-child(1)
  border-right-width 1px
.pwd_input
  width ($inputLength * 6)
  height $inputLength
  padding-right (($inputLength - $dottedWidth - .12rem/* 6px */) / 2)
  border none
  opacity 0
  text-align right
  z-index 9
</style>
