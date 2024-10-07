<template>
    <button class="button" :style="buttonStyle" >
        <Icon name="icon-park-outline:right-c" color="white" size="20"/>
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
    padding: 8px;
    border-radius: 4px;
    font-family: Impact;
    font-size: 14px;
    font-weight: 400;
    line-height: 20px;
    letter-spacing: 1px;
    text-align: center;
    text-transform: uppercase;
    display: flex;
  }
  </style>