<template>
  <div class="theRamParent">
    <div class="ramBox">
      <div class="ramIco">
        <div class="ramIco-container">
          <img src="../../../../public/img/icon/control/ramStick.svg" />
        </div>
        <span>{{ $t("controlPage.ram") }}</span>
      </div>
      <div class="ramValue">
        <div class="valDigits">
          <div class="digits">
            <span>{{ usedRam }} / {{ totalRam }}</span>
          </div>
          <span>MB</span>
        </div>
        <div class="valLbl">
          <span>{{ $t("controlPage.used") }}</span
          ><span>{{ $t("controlPage.totalram") }}</span>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import { mapState } from "pinia";
import { useControlStore } from "../../../store/theControl";
export default {
  data() {
    return {};
  },
  computed: {
    ...mapState(useControlStore, {
      usedRam: "usedRam",
      totalRam: "totalRam",
    }),
  },
};
</script>

<style scoped>
.theRamParent {
  display: flex;
  width: 100%;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  box-sizing: border-box;
  height: 100%;
}
.ramBox {
  width: 100%;
  height: 100%;
  display: flex;
  box-sizing: border-box;
}
.ramIco {
  box-sizing: border-box;
  width: 30%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}
.ramIco span {
  width: 100%;
  height: 20%;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 60%;
  font-weight: bold;
  color: #c1c1c1;
}
.ramIco-container {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 80%;
}
.ramIco-container img {
  width: 75%;
}
.ramValue {
  width: 70%;
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
.valDigits {
  display: flex;
  width: 100%;
  height: 70%;
  justify-content: center;
  align-items: center;
  color: #c1c1c1;
}
.digits {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 70%;
  height: 100%;
}
.valDigits,
.digits span {
  font-size: 1rem;
  font-weight: 600;
  color: #c1c1c1;
}
.valLbl {
  display: flex;
  width: 40%;
  align-items: center;
  justify-content: space-between;
  font-size: 0.7rem;
  font-weight: 500;
  color: #c1c1c1;
}
</style>
