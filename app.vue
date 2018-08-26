<template>
  <div>
    <ButtonGroup>
      <Button @click="click">
        提交a
      </Button>
      <Button @click="click" :icon="'icon-down'">
        提交a
      </Button>
      <Button @click="click" :icon="'icon-down'" :dir="'r'">
        提交a
      </Button>
      <Button @click="load=!load" :loading="load">
        加载中
      </Button>
      <Button @click="load=!load" :loading="load" :dir="'r'">
        加载中
      </Button>
      <p>11111111</p>
    </ButtonGroup>
  </div>
</template>
<script>
import './src/js/iconfont.js'
import Vue from 'vue'
import Button from './src/base/Button'
Vue.component('Button', Button)
import svgIcon from './src/base/svgIcon'
Vue.component('svgIcon', svgIcon)
import ButtonGroup from './src/base/ButtonGroup'
Vue.component('ButtonGroup', ButtonGroup)
export default {
  data() {
    return {
      load: true
    }
  },
  methods: {
    click() {}
  }
}
</script>

<style lang="scss">
@import './src/scss/index.scss';
</style>
