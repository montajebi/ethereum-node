<template>
  <section class="BtnInstIcon">
    <div class="imgIcon" @mouseover="isHovered = true" @mouseleave="isHovered = false">
      <img v-if="isHovered" :src="url" />
      <img v-else :src="img" />
    </div>
  </section>
</template>
<script>
export default {
  name: "ButtonInstallation",
  props: {
    img: {
      type: String,
      required: true,
    },
    url: {
      type: String,
      required: true,
    },
  },
  data() {
    return {
      isHovered: false,
    };
  },
};
</script>
<style scoped>
.BtnInstIcon {
  width: 100%;
  height: 100%;
  border-radius: 50px;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
  align-items: center;
  z-index: -1;
}

.imgIcon {
  width: 100%;
  display: flex;
  border-radius: 50px;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.imgIcon img {
  width: 95%;
  height: 100%;
  resize: both;
  border-radius: 50px;
  border: 4px solid  #1e2429;
  cursor: pointer;
}

.text-color {
  color: #333 !important;
}
</style>
