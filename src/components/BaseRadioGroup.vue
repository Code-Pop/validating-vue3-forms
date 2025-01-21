<template>
  <div>
    <component
      :is="vertical ? 'div' : 'span'"
      v-for="opts in options"
      :key="opts.value"
      :style="vertical ? '' : 'margin-right: 20px;'"
    >
      <BaseRadio
        :name="name"
        :label="opts.label"
        :model-value="modelValue"
        :value="opts.value"
        @update:model-value="$emit('update:modelValue', $event)"
      />
    </component>
  </div>
</template>

<script>
export default {
  props: {
    vertical: {
      type: Boolean,
      default: false
    },
    modelValue: {
      type: [String, Number],
      required: true
    },
    options: {
      type: Array,
      required: true
    },
    name: {
      type: String,
      required: true
    }
  }
}
</script>
