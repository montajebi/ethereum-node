<template>
  <div>
    <div class="bg-opacity"></div>
    <div class="removeRow"></div>
  </div>
</template>
<script>
export default {};
</script>
<style scoped>
.removeRow {
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #a3111192;
  opacity: 0.9;
  border-radius: 50px;
  position: absolute;
  pointer-events: none;
  z-index: 100;
}
.bg-opacity {
  width: 100%;
  height: 100%;
  position: fixed;
  top: 0;
  left: 0;
  z-index: 101;
}
</style>
