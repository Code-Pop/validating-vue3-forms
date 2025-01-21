<template>
  <p
    :id="id"
    aria-live="assertive"
    class="errorMessage"
  >
    <slot />
  </p>
</template>

<script>
export default {
  props: {
    id: {
      type: [String, Number],
      required: true
    }
  }
}
</script>
