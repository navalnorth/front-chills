<template>
  <button :style="buttonStyle">
    <slot></slot>
  </button>
</template>

<script setup>
const props = defineProps({
  textColor: {
    type: String,
    default: ''
  },
  backgroundColor: {
    type: String,
    default: ''
  },
  borderColor: {
    type: String,
    default: ''
  }
});

const buttonStyle = computed(() => ({
  color: props.textColor,
  backgroundColor: props.backgroundColor,
  border: `2px solid ${props.borderColor}`,
  padding: '8px 16px',
  borderRadius: '5px',
  fontFamily: 'Impact',
  cursor: 'pointer'
}));
</script>