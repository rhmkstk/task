<script>
export default {
  name: "BaseButton",
  props: {
    bgColor: {
      type: String,
      default: "#375673",
    },
  },
};
</script>

<template>
  <button
    class="base-button"
    :style="`background-color: ${bgColor}`"
    v-bind="$attrs"
  >
    <slot />
  </button>
</template>

<style scoped>
.base-button {
  padding: 11px 16px;
  border-radius: 4px;
  color: #ffffff;
  font-size: 12px;
   white-space: nowrap;
}
</style>
