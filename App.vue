<template>
  <h2 @[event]='add'>{{ msg }}</h2>
  <h2 v-bind:[attr]='message'>{{ message }}</h2>
  <Fruits/>
  <h2>{{ reversedMessage }}</h2>
  <h2 :class="{active: isActive}" @click="activate">Hello???({{ isActive }})</h2>
  <h2 :style="fontStyle" @click="changeStyle">Hi</h2>
  <h2 v-if="isShow">click button</h2>
  <h2 v-else>Good~!!</h2>
  <button @click="handler">click me!</button>
  <h1>My Favorit Fruits</h1>
  <ul>
    <li v-for="(A, index) in B" :key="A">{{ A }}-{{ index + 1 }}</li>
  </ul>
</template>

<script>
import Fruits from './components/Fruits.vue'

export default {
  components: { Fruits },
  
  data() {
    return {
      B: ['Watermelon', 'Melon', 'Orange'],
      isShow: true,
      fontStyle: {
        color: 'orange',
        fontSize: '30px',
      },
      isActive: false,
      alert: 'hello computed!',
      msg: 'hello world!',  
      message: 'action',
      attr: 'class',
      event: 'click'
    }
  },

  component: {
    Fruits
  },

  computed: {
    reversedMessage() {
      return this.alert.split('').reverse().join('')
    },
  },

  methods: {
    add() {
    this.msg += '!'
    },

    activate() {
    this.isActive = true
    },

    changeStyle() {
      this.fontStyle.color = 'blue'
      this.fontStyle.fontSize = '50px'
    },

    handler() {
      this.isShow = !this.isShow
    },
  },
}
</script>

<style scoped>
  .action {
    color: royalblue;
  }

  .active{
    color : red;
    font-weight: bold;
  }
</style>