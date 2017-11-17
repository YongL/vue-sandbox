<template>
  <input
    type="text"
    class="input"
    :value="value"
    v-on="$listeners"
    @input="$emit('input', $event.target.value )"
  >
</template>

<script>
export default {
  props: {
    value: {
      type: String,
      default: '',
    }
  }
}
</script>


