<template>
  <div>
    <div id="a">
    </div>
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
import svgIcon from './src/base/svgIcon'
import Button from './src/base/Button'
import ButtonGroup from './src/base/ButtonGroup'
Vue.component('svgIcon', svgIcon)
Vue.component('Button', Button)
Vue.component('ButtonGroup', ButtonGroup)
//test
import chai from 'chai'
import spies from 'chai-spies'
chai.use(spies)
let expect=chai.expect

export default {
  data() {
    return {
      load: true
    }
  },
  methods: {
    click() {}
  },
  mounted() {
    {
      let GButton = Vue.extend(Button)
      let b = new GButton({
        propsData: {
          icon: 'icon-down'
        }
      })
      b.$mount()
      expect(b.$el.querySelector('use').getAttribute('xlink:href')).to.equal(
        '#icon-down'
      )
      b.$el.remove()
      b.$destroy()
    }
    {
      let div = document.createElement('div')
      document.body.appendChild(div)
      let GButton = Vue.extend(Button)
      let b = new GButton({
        propsData: {
          icon: 'icon-down',
          dir: 'r'
        }
      })
      b.$mount(div)
      let svg = b.$el.querySelector('svg')
      let { order } = window.getComputedStyle(svg)
      expect(order).to.equal('1')
      b.$el.remove()
      b.$destroy()
    }
    {
      let div = document.createElement('div')
      document.body.appendChild(div)
      let GButton = Vue.extend(Button)
      let b = new GButton({
        propsData: {
          icon: 'icon-down',
          dir: 'r'
        }
      })
      b.$mount(div)
      let spy = chai.spy(() => {
      })
      b.$on('click',spy)
      b.$el.click()
      expect(spy).have.been.called()
      b.$el.remove()
      b.$destroy()
    }
  }
}
</script>

<style lang="scss">
@import './src/scss/index.scss';
</style>
