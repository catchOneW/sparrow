<template>
    <div>
        <slot>

        </slot>
    </div>
</template>

<script>
export default {
  props: {
    prop: String
  },
  mounted() {
    if (this.prop) {
      this.dispatch('ElForm', 'el.form.addField', [this])

      let initialValue = this.fieldValue
      if (Array.isArray(initialValue)) {
        initialValue = [].concat(initialValue)
      }
      Object.defineProperty(this, 'initialValue', {
        value: initialValue
      })

      let rules = this.getRules()

      if (rules.length || this.required !== undefined) {
        this.$on('el.form.blur', this.onFieldBlur)
        this.$on('el.form.change', this.onFieldChange)
      }
    }
  }
}
</script>

<style>
</style>
