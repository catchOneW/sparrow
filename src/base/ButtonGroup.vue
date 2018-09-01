<template>
    <div class="btn-group">
        <slot></slot>
    </div>
</template>

<script>
export default {
  mounted() {
    //  console.log(this.$el.children);
      
    for (const node of this.$el.children) {
        if(node.nodeName.toLowerCase()!=='button'){
            console.warn('子元素不是button');
        }
    }
  }
}
</script>

<style lang="scss" scoped>
.btn-group {
  .btn {
  }
}
</style>

