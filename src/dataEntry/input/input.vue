<template>
    <div>
        <input :value="value"
               @input="$emit('input',$event.target.value)"
               type="text">
    </div>
</template>

<script>
export default {
  props: ['value'],
  data() {
    return {}
  }
}
</script>

<style>
</style>
