<template>
  <div id="tab-bar">
    <slot></slot>
  </div>
</template>

<script>
  export default {
    name: "TabBar"
  }
</script>

<style scoped>
  #tab-bar {
    display: flex;
    background: #f6f6f6;
    height: 49px;
    text-align: center;
    position: fixed;
    left: 0;
    right: 0;
    bottom: 0;
    box-shadow: -1px 1px 13px 0px rgba(0, 0, 0, 0.1);
    font-size: 14px;
  }

</style>
