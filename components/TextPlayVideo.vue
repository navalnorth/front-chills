<template>
    <button class="button" :style="buttonStyle" >
      <slot></slot>
      <Icon name="bi:play-btn" />
    </button>
  </template>
  
  <script setup>
  const props = defineProps({
    textColor: {
      type: String,
      default: ''
    },
    background: {
      type: String,
      default: ''
    },
    borderSolid: {
      type: String,
      default: ''
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
    font-size: 14px;
    font-weight: 100;
    line-height: 20px;
    letter-spacing: 1px;
    text-align: center;
    text-transform: uppercase;
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 4px;
  }
  </style>