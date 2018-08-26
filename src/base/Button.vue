<template>
  <button class="btn h32 bd" @click="$emit('click')">
    <svgIcon class="vam" v-if="icon&&loading===undefined" :icon="icon" :class="{'icon-l':dir=='l','icon-r':dir=='r'}"></svgIcon>
    <svgIcon class="vam" v-if="loading!==undefined" :icon="'icon-Loading'" :class="{'icon-l':dir=='l','icon-r':dir=='r','icon-loading':loading}"></svgIcon>
    <slot></slot>
  </button>
</template>

<script>
export default {
  props: {
    icon: {},
    dir: {
      default: 'l'
    },
    loading: {
      default: undefined
    }
  }
}
</script>
<style lang="scss" scoped>
.btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  padding: 0 1em;
  border-radius: 4px;
  &:hover {
    background-color: #ccc;
  }
  &:active {
    background-color: #ccc;
  }
  .icon-l {
    margin-right: 0.5em;
  }
  .icon-r {
    order: 1;
    margin-left: 0.5em;
  }
  .icon-loading {
    animation: circle 1s linear infinite;
  }
  @keyframes circle {
    0% {
      transform: rotate(0deg);
    }
    100% {
      transform: rotate(360deg);
    }
  }
}
</style>
