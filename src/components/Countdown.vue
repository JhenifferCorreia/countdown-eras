<script setup lang="ts">
import { onMounted, ref } from "vue";

const days = ref(0);
const hours = ref(0);
const minutes = ref(0);
const seconds = ref(0);
const countDownDate = ref(new Date("2023-11-17T00:00").getTime());

onMounted(() => {
  getTime();
});

function getTime() {
  CountDown();
}

function CountDown() {
  setInterval(() => {
    const now = new Date().getTime();

    const distance = Number(countDownDate.value) - now;

    days.value = Math.floor(distance / (1000 * 60 * 60 * 24));
    hours.value = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
    minutes.value = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60));
    seconds.value = Math.floor((distance % (1000 * 60)) / 1000);
  }, 1000);
}

function updateCountdown(dateString: string) {
  countDownDate.value = new Date(dateString)!.getTime();
}

function formatedDays() {
  return String(days.value).padStart(2, '0');
}

function formatedHours() {
  return String(hours.value).padStart(2, '0');
}

function formatedMinutes() {
  return String(minutes.value).padStart(2, '0');
}

function formatedSeconds() {
  return String(seconds.value).padStart(2, '0');
}


</script>

<template>
  <div>
    <div class="countdown">
      <p>{{ formatedDays() }}:{{ formatedHours() }}:{{ formatedMinutes() }}:{{ formatedSeconds() }}</p>
    </div>

    <div>
      <div class="rj">
        <button id="fearless" @click="updateCountdown('2023-11-17T00:00')">RJ 17/11</button>
        <button id="red" @click="updateCountdown('2023-11-18T00:00')">RJ 18/11</button>
        <button id="reputation" @click="updateCountdown('2023-11-19T00:00')">RJ 19/11</button>
      </div>
      <div class="sp">
        <button id="evermore" @click="updateCountdown('2023-11-24T00:00')">SP 24/11</button>
        <button id="lover" @click="updateCountdown('2023-11-25T00:00')">SP 25/11</button>
        <button id="midnights" @click="updateCountdown('2023-11-26T00:00')">SP 26/11</button>
      </div>
    </div>
  </div>
</template>


<style scoped>
p {
  font-family: "Pistilli-Roman";
  font-size: clamp(3rem, 0.2782rem + 4.8387vw, 3.375rem);
}

.countdown {

  margin-bottom: 3.5em;
}


#fearless {
  background-color: #F2C483;
}

#red {
  background-color: #813C48;
}

#reputation {
  background-color: #767173;
}

#evermore {
  background-color: #C8B095;
}

#lover {
  background-color: #F7B2CD;
}

#midnights {
  background-color: #303850;
}
</style>
