<template>
  <button class="g-button">提交</button>
</template>

<script>
export default {}
</script>

<style lang="scss">
.g-button {
  height: var(--h);
  font-size: var(--fs);
  padding: 0 1em;
  border-radius: 4px;
  &:hover {
    border: 1px solid red;
  }
  &:active {
    background-color: #fff;
  }
}
</style>
