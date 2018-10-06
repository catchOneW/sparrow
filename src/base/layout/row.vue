<template>
  <div class="df"
       :style="gutterStyle">
    <slot></slot>
  </div>
</template>

<script>
export default {
  props: ['gutter'],
  data() {
    return {}
  },
  computed: {
    gutterStyle() {
      return {
        marginLeft: `-${this.gutter / 2}px`,
        marginRight: `-${this.gutter / 2}px`
      }
    }
  },
  mounted() {
    if (this.gutter) {
      this.$children.forEach(vm => {
        vm.gutter = this.gutter
      })
    }
  }
}
</script>

<style lang="scss" scoped>

</style>
