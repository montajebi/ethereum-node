<template>
  <div class="parent">
    <div class="header">
      <span>One Click Installation</span>
    </div>
    <div class="containerOption">
      <div class="text">
        {{ $t("installOption.installText") }}
      </div>
      <div class="plugin-container">
        <NetworkSelect @disable-btn="enableButtonHandler" />
      </div>
    </div>
    <div class="btn-container">
      <router-link class="back" :to="{ path: '/welcome' }">
        <span id="back">{{ $t("installOption.back") }}</span>
      </router-link>
      <div v-if="isButtonEnabled" class="install" @click="clickedToInstall">
        <span>
          {{ $t("installOption.install") }}
        </span>
      </div>
    </div>
  </div>
</template>

<script>
import NetworkSelect from "./NetworkSelect.vue";
import { mapState } from "pinia";
import { useClickInstall } from "@/store/clickInstallation";
export default {
  components: {
    NetworkSelect,
  },
  data() {
    return {
      isButtonEnabled: false,
    };
  },
  computed: {
    ...mapState(useClickInstall, {
      selectedPreset: "selectedPreset",
    }),
  },
  methods: {
    enableButtonHandler() {
      this.isButtonEnabled = true;
    },
    clickedToInstall() {
      if (Object.keys(this.selectedPreset).length > 0) {
        this.$router.push("/install");
      }
    },
  },
};
</script>

<style scoped>
* {
  box-sizing: border-box;
}

.parent {
  width: 100vw;
  height: 100vh;
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  grid-template-rows: 10% 15% 60% 25%;
}
.header {
  grid-column: 2/5;
  grid-row: 2/3;
  margin: 0 auto;
  background-color: #2d3134;
  border: 3px solid #b4b4b4;
  border-radius: 15px;
  width: 100%;
  height: 80%;
  text-align: center;
  font-size: 1.5rem;
  color: rgb(214, 214, 214);
  font-weight: 700;
  position: relative;
  box-shadow: 0 1px 3px 1px rgb(46, 57, 55);
  display: flex;
  justify-content: center;
  align-items: center;
  text-transform: uppercase;
}

.containerOption {
  grid-column: 2/5;
  grid-row: 3/4;
  width: 100%;
  height: 100%;
  margin: 0 auto;
  padding: 10px;
  background-color: #2d3134;
  border: 3px solid #b4b4b4;
  border-radius: 20px;
  position: relative;
  box-shadow: 0 1px 3px 1px rgb(25, 33, 32);
}
.plugin-container {
  width: 100%;
  height: 100%;
  overflow: hidden;
}

.container p {
  text-align: center;
  width: 95%;
}

.text {
  width: 90%;
  margin: 2% auto;
  font-size: 0.9rem;
  color: rgb(200, 200, 200);
  font-weight: 400;
  text-align: justify;
}
.select-box {
  width: 50%;
  margin: 0 auto;
}
.btn-container {
  grid-column: 1/6;
  grid-row: 4/5;
  width: 80%;
  height: 40%;
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin: 0 auto;
}

.back,
.install {
  height: 40px;
  min-width: 120px;
  border-radius: 40px;
  border: 3px solid #929292;
  background-color: #194747;
  font-size: 1.2rem;
  font-weight: 700;
  color: rgb(191, 191, 191);
  box-shadow: 0 1px 3px 1px rgb(41, 61, 51);
  outline-style: none;
  cursor: pointer;
  display: flex;
  justify-content: center;
  align-items: center;
}
.install:hover,
.back:hover {
  background-color: rgb(31, 48, 43);
  box-shadow: 0 1px 3px 0 rgb(21, 31, 26);
}
.install:active,
.back:active {
  box-shadow: inset 1px 1px 3px 1px rgb(14, 19, 17);
}
.disabledBtn {
  width: auto;
  min-width: 120px;
  height: 70%;
  resize: both;
  border: 3px solid #545454;
  border-radius: 40px;
  background-color: rgb(50, 71, 65) !important;
  font-size: 1.3rem;
  box-shadow: none !important;
  font-weight: 800;
  color: rgb(135, 135, 135) !important;
  outline-style: none;
}
</style>
