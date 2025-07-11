<template>
  <div>

    <section>
      <div class="clock">
        <div class="container">
          <h2 id="hour">00</h2>
          <h2 class="dot">:</h2>
          <h2 id="minute">00</h2>
          <h2 class="dot">:</h2>
          <h2 id="seconds">00</h2>
          <span id="ampm">AM</span>
        </div>
      </div>
    </section>

  </div>
</template>

<script setup>
import { onMounted } from "vue"

const clock = () => {
  const hour = document.getElementById('hour')
  const minute = document.getElementById('minute')
  const seconds = document.getElementById('seconds')
  const ampm = document.getElementById('ampm')

  let h = new Date().getHours()
  const m = new Date().getMinutes()
  const s = new Date().getSeconds()
  let am = 'AM'

  // Convert 24 hour time to 12 hour format with AM PM indicator
  if(h > 12){
    h = h - 12
    am = 'PM'
  }


  // Add '0' if value < 10
  hour.innerHTML = h < 10 ? '0' + h : h;
  minute.innerHTML = (m < 10) ? '0' + m : m;
  seconds.innerHTML = (s < 10) ? '0' + s : s;
  ampm.innerHTML = am
}

onMounted(() => {
  setInterval(clock, 1000)
})
</script>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: consolas;
}

section {
  position: relative;
  width: 100%;
  height: 100vh;
  background: #19172e;
  display: flex;
  justify-content: center;
  align-items: center;
}

section::before {
  content: '';
  position: absolute;
  top: 10%;
  right: 20%;
  width: 300px;
  height: 300px;
  border-radius: 10px;
  background: linear-gradient(#f9d924,#ff2c24);
  animation: animate 5s ease-in-out infinite;
}

section::after {
  content: '';
  position: absolute;
  bottom: 10%;
  left: 20%;
  width: 250px;
  height: 250px;
  border-radius: 10px;
  background: linear-gradient(#01d6ff,#0f24f9);
  animation: animate 5s ease-in-out infinite;
  animation-delay: -2.5s;
}

@keyframes animate {
  0%
  {
    transform: translateY(20px);
  }
  50%
  {
    transform: translateY(-20px);
  }
}
.clock {
  position: relative;
  width: 700px;
  height: 250px;
  background: rgba(255, 255, 255, 0.05);
  box-shadow: 0 15px 25px rgba(0,0,0,0.1);
  z-index:1000;
  border-radius: 20px;
  border: 1px solid rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(20px);
}

.clock .container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100%;
}

.clock .container h2 {
  font-size: 6em;
  color: #fff;

}

.clock .container h2:nth-child(odd) {
  padding: 5px 15px;
  border-radius: 10px;
  background: rgba(255, 255, 255, 0.05);
  box-shadow: 0 15px 25px rgba(0,0,0,0.2);
  margin: 0 10px;
  border-bottom: 1px solid rgba(255, 255, 255, 0.1);
  border-right: 1px solid rgba(255, 255, 255, 0.1);
}

.clock .container h2#seconds {
  color: #f9d524;
}

#ampm{
  position: relative;
  top: -50px;
  color: #fff;
  font-weight: 700;
}
</style>
