<template>
  <div class="contributor-parent">
    <div class="contributor-avatar"><img :src="avatar" /></div>
    <div class="contributor-name">
      <span>{{ name }}</span>
    </div>
  </div>
</template>
<script>
export default {
  props: {
    name: {
      type: String,
      required: true,
      default: "",
    },
    avatar: {
      type: String,
      required: true,
      default: "",
    },
  },
};
</script>
<style scoped>
.contributor-parent {
  display: flex;
  width: 100%;
  height: 100%;
  justify-content: flex-start;
  align-items: center;
  border: 1px solid #343131;
  background: #2a2a2a;
  box-sizing: border-box;
  box-shadow: 1px 1px 10px 1px rgb(23, 23, 23);
  border-radius: 30px;
}
.contributor-parent:hover {
  background: #313131;
}
.contributor-avatar {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 25%;
  height: 100%;
}
.contributor-avatar img {
  width: 90%;
  border-radius: 50%;
}
.contributor-name {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 75%;
  height: 10%;
  font-size: 100%;
  font-weight: 400;
  color: #eee;
}
</style>
