<script setup>
import { ref } from "vue";
const emit = defineEmits(["onTimerPositionChenge"]);

const minutes = ref(0);
const seconds = ref(0);
const launchTime = ref(3000);

const timer = setInterval(() => {
   const currDate = 1000;
   launchTime.value -= currDate;
   seconds.value = parseInt(launchTime.value / 1000);
   minutes.value = parseInt(seconds.value / 60);
   if (seconds.value === 0) {
      emit("onTimerPositionChenge");
      clearInterval(timer);
   }
}, 1000);
</script>

<template>
   <div class="timer">
      <span v-if="minutes % 60 > 9">{{ minutes % 60 }}</span>
      <span v-else>0{{ minutes % 60 }}</span>
      <span> : </span>
      <span v-if="seconds % 60 > 9">{{ seconds % 60 }}</span>
      <span v-else>0{{ seconds % 60 }}</span>
   </div>
</template>

<style scoped>
.timer {
   margin: 0 auto;
   height: 30px;
   width: 200px;
   text-align: center;
   line-height: 30px;
   border-radius: 5px;
   background: rgba(255, 0, 0, 0.449);
}
</style>
