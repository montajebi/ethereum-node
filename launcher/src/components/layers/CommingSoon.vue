<template>
  <div class="commingsoon-parent">
    <span>- {{ $t("comingsoon.comingsoon") }} -</span>
  </div>
</template>
<style scoped>
.commingsoon-parent {
  width: 100%;
  height: 100%;
  display: flex;
  position: absolute;
  justify-content: center;
  align-items: center;
  border: 1px solid #343434;
  background: rgba(85, 87, 85, 0.7);
  font-weight: 600;
  color: aqua;
  font-size: 70%;
  pointer-events: none;
  z-index: 0;
}
</style>
