<template>
    <div :class="`el-col-${span}`"
         :style="gutterStyle">
        <slot></slot>
    </div>
</template>

<script>
export default {
  props: ['span'],
  data() {
    return {
      gutter: 0,
    }
  },
  computed: {
    gutterStyle() {
      return {
        paddingLeft: `${this.gutter / 2}px`,
        paddingRight: `${this.gutter / 2}px`
      }
    }
  }
}
</script>

<style lang="scss" scoped>
@for $n from 1 to 25 {
  .el-col-#{$n} {
    width: $n * 100/24#{'%'};
    box-sizing: border-box;
  }
}
</style>

