<template>
  <button class="button" :style="buttonStyle" >
    <slot></slot>
  </button>
</template>

<script setup>
const props = defineProps({
  textColor: {
    type: String,
    default: 'var(--text-color-light)'
  },
  background: {
    type: String,
    default: 'var(--border-none)'
  },
  borderSolid: {
    type: String,
    default: 'var(--border-none)'
  }
});

const buttonStyle = computed(() => ({
  color: props.textColor,
  background: props.background,
  border: `${props.borderSolid}`,
}));
</script>

<style scoped>
.button {
  cursor: pointer;
  padding: 8px 16px;
  border-radius: 4px;
  font-family: Impact;
  font-size: 16px;
  font-weight: 300;
  line-height: 20px;
  letter-spacing: 1px;
  text-align: center;
  text-transform: uppercase;
  letter-spacing: 2.4px
}
</style>