<template>
  <div class="attestationParent divide-y divide-gray-600">
    <div class="attestationSlot">
      <div class="attestation_last">
        <div class="attestation_last_title">
          <span>{{ $t("theAttes.lastAttest") }}</span>
        </div>
        <div class="attestation_last_value">
          <span v-if="stats.ETA === ''">{{ stats.attestationSlot }}</span>
          <span v-else :class="{ isOnline: attestationIsOnline }">{{ stats.currentSlot }}</span>
        </div>
      </div>
      <div class="keyStatus">
        <div class="keyStatus_title">
          <span>{{ $t("theAttes.keyStatus") }}</span>
        </div>
        <div class="keyStatus_value">
          <span v-if="stats.ETA === ' ETA: now!'" class="text-[12px] font-semibold text-green-400">{{
            $t("theAttes.attest")
          }}</span>
          <span v-else-if="stats.ETA == undefined || stats.ETA == null" class="text-[10px] text-yellow-400">{{
            $t("theAttes.noKey")
          }}</span>
          <span v-else class="text-[12px] font-semibold text-red-500">{{ $t("theAttes.pending") }}</span>
        </div>
      </div>
    </div>
    <div class="attestationNext">
      <div class="attestation_next">
        <div class="attestation_next_title">
          <span>{{ $t("theAttes.nxtAttest") }}</span>
        </div>
        <div class="attestation_next_value">
          <span v-if="stats.ETA === ''">----</span>
          <span v-else-if="stats.ETA === ' ETA: now!'">----</span>
          <span v-else :class="{ isOnline: attestationIsOnline }">{{ stats.attestationSlot }}</span>
        </div>
      </div>
      <div class="remainingStatus">
        <div class="remaining_title">
          <p v-if="attestationIsOnline">
            <span>{{ stats.remainingSlots }}</span> {{ $t("theAttes.slotRem") }}
          </p>
          <p v-else><span>??</span> {{ $t("theAttes.slotRem") }}</p>
        </div>
        <div class="remaining_time">
          <!-- <p v-if="attestationIsOnline">
            <span>{{ stats.remainingTime }}</span> till attestation
          </p>
          <p v-else><span>??</span> till attestation</p> -->
          <p>
            <span>{{ getRemainingTime }}</span> {{ $t("theAttes.tillAtest") }}
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { mapState } from "pinia";
import { useStakingStore } from "../../../store/theStaking";
export default {
  data() {
    return {
      attestationIsOnline: true,
      remainingTime: "",
    };
  },
  computed: {
    ...mapState(useStakingStore, {
      keys: "keys",
      stats: "stats",
    }),

    getRemainingTime() {
      if (this.stats.ETA === "") {
        return "";
      } else if (this.stats.ETA === " ETA: now!") {
        return "";
      } else {
        return `${this.stats.remainingTime ? this.stats.remainingTime : "-"} sec`;
      }
    },
  },
};
</script>

<style scoped>
.attestationParent {
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
  align-items: center;
  width: 100%;
  height: 100%;
  padding: 5px 0;
}
.attestationSlot,
.attestationNext {
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
  align-items: center;
  width: 100%;
  height: 50%;
  text-transform: capitalize;
}
.attestation_last,
.keyStatus,
.attestation_next {
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-template-rows: 1fr;
  width: 100%;
  height: 50%;
}
.attestationSlot .attestation_last_title,
.attestationNext .attestation_next_title {
  grid-column: 1/2;
  grid-row: 1;
  width: max-content;
  height: 100%;
  display: flex;
  justify-content: flex-start;
  align-items: center;
}
.attestationSlot .attestation_last_title span,
.attestationNext .attestation_next_title span {
  color: #e0e0e0;
  font-size: 0.6rem;
  font-weight: 500;
}
.attestationSlot .attestation_last_value,
.attestationNext .attestation_next_value {
  grid-column: 2/3;
  grid-row: 1;
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: flex-end;
  align-items: center;
}
.attestationSlot .attestation_last_value span,
.attestationNext .attestation_next_value span {
  color: #e0e0e0;
  font-size: 0.7rem;
  font-weight: 600;
}
.attestationSlot .keyStatus_title {
  grid-column: 1/2;
  grid-row: 1;
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: flex-start;
  align-items: center;
}
.attestationSlot .keyStatus_title span {
  color: #e0e0e0;
  font-size: 0.6rem;
  font-weight: 500;
}
.attestationSlot .keyStatus_value {
  grid-column: 2/3;
  grid-row: 1/2;
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: flex-end;
  align-items: center;
}
/* .attestationSlot .keyStatus_value span {
  color: #ec3939;
  font-size: 0.6rem;
  font-weight: 600;
} */
.attesting {
  color: #35bf35 !important;
}
.isOnline {
  color: #35bf35 !important;
}
.remainingStatus {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-template-rows: 2fr;
  width: 100%;
  height: 50%;
}
.remaining_title {
  grid-column: 1/4;
  grid-row: 1/2;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 50%;
}
.remaining_title p {
  display: flex;
  justify-content: flex-end;
  align-items: center;
  width: 100%;
  height: 100%;
  color: #e0e0e0;
  font-size: 0.6rem;
  font-weight: 500;
}
.remaining_title p span {
  color: #e6e331 !important;
  font-size: 0.6rem;
  font-weight: 500;
  margin-right: 2px;
}

.remainingStatus .remaining_time {
  grid-column: 1/4;
  grid-row: 2/3;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 50%;
}
.remainingStatus .remaining_time p {
  display: flex;
  justify-content: flex-end;
  align-items: center;
  width: 100%;
  height: 100%;
  color: #e0e0e0;
  font-size: 0.6rem;
  font-weight: 500;
}
.remainingStatus .remaining_time p span {
  color: #e6e331 !important;
  font-size: 0.6rem;
  font-weight: 500;
  margin-right: 2px;
}

.activeRemaining {
  color: #e6e331 !important;
}
</style>
