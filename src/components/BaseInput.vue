<script>
export default {
  name: "BaseInput",
  props: {
    modelValue: {
      type: String,
      default: "",
    },
  },
  emits: ["update:modelValue"],
};
</script>

<template>
  <input
    class="base-input"
    v-bind="$attrs"
    :value="modelValue"
    @input="$emit('update:modelValue', $event.target.value)"
  />
</template>

<style scoped>
.base-input {
  padding: 8px 12px;
  border: 1px solid #e0e2e4;
  border-radius: 4px;
  color: #939597;
  font-size: 14px;
}
</style>
