<template>
  <div>
    <!-- <ButtonGroup>
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
    </ButtonGroup> -->

    <!-- <el-form ref="formRef" :model="obj" :rules="ruleObj">
      <input type="text" name="a">
      <input type="button" value="验证" @click="$refs['formRef'].validate()">
    </el-form> -->
    <el-input v-model="a"
              placeholder="请输入内容"></el-input>
<button @click="loga">log</button>
  </div>
</template>
<script>
import './src/js/iconfont.js'
import Vue from 'vue'
import chai from 'chai'
import spies from 'chai-spies'
chai.use(spies)
let expect = chai.expect

import svgIcon from './src/base/svgIcon'
import Button from './src/base/Button'
import ButtonGroup from './src/base/ButtonGroup'
import Form from './src/dataEntry/Form'
import { input } from './src/dataEntry/input'
Vue.component('svgIcon', svgIcon)
Vue.component('Button', Button)
Vue.component('ButtonGroup', ButtonGroup)
Vue.component('el-form', Form)
Vue.component('el-input', input)
export default {
  data() {
    return {
      a: 1,
      load: true,
      //
      obj: {
        a: 1111
      },
      ruleObj: {
        a: { required: true, message: '请输入活动名称', trigger: 'blur' }
      }
    }
  },
  methods: {
    loga(){
        console.log(this.a);
        
    },
    test() {
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
        let spy = chai.spy(() => {})
        b.$on('click', spy)
        b.$el.click()
        expect(spy).have.been.called()
        b.$el.remove()
        b.$destroy()
      }
    }
  },
  mounted() {
    //this.test()
  }
}
</script>

<style lang="scss">
@import './src/scss/index.scss';
</style>
