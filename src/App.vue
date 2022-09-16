<script setup>
import { onMounted, ref } from "vue";
import CalendarAndClock from "./components/CalendarAndClock.vue";
import { Confetti } from "./components/util";

window.onload = function () {
  //canvas init
  var canvas = document.getElementById("confetti");
  var ctx = canvas.getContext("2d");
  Confetti(canvas, ctx);

  // window.resizeWindow = function() {
  //   Confetti();
  // };

  // window.addEventListener('resize', resizeWindow, false);
};

// 获取页面高度
const getPageHeight = function () {
  const pageHeight = window.innerHeight;
  document.querySelector(".notes").style.height = `${pageHeight - 100}px`;
  console.log(
    "calendar height",
    document.querySelector("div.calendar").clientHeight
  );
  console.log(
    "calendar width",
    document.querySelector("div.calendar").clientWidth
  );
};

window.addEventListener("resize", getPageHeight);
onMounted(() => {
  getPageHeight();
});
</script>

<template>
  <header>
    <h2>
      <!-- <span>&hearts;&nbsp;</span>Love Anniversary<span>&nbsp;&heartsuit;</span> -->
      <span>&hearts;&nbsp;</span>Anniversary<span>&nbsp;&heartsuit;</span>
    </h2>
  </header>

  <main>
    <div class="container">
      <div class="date">
        <div class="calendar">
          <CalendarAndClock></CalendarAndClock>
          
        </div>
        <div class="how-long"></div>
      </div>
      <div class="notes"></div>
    </div>
  </main>

  <footer>
    <!-- <p>Chen<span>&nbsp;&hearts;&nbsp;</span>Hao</p> -->
    <p>HELLO</p>
  </footer>
  <!-- <canvas id="confetti"></canvas> -->
</template>

<style scoped>
header > h2,
footer > p {
  padding-top: 5px;
  margin: 0;
  text-align: center;
  font-size: 3rem;
  font-family: "Concert One", cursive;
  color: #80d1c8;
}
header,
footer {
  align-items: center;
  justify-content: center;
  min-height: 5rem;
  background-color: #f8f5d6;
}
.container {
  display: grid;
  grid-template-columns: 0.382fr 0.618fr;
  grid-auto-rows: minmax(400px, auto);
  grid-gap: 2px;
  gap: 2px;
}
.calendar,
.how-long,
.notes {
  margin: 5px;
  background-color: #eee;
  border-radius: 5px;
  border: 0px solid gray;
}
.date {
  display: grid;
  grid-gap: 2px;
  gap: 2px;
  grid-template-columns: 1fr;
  grid-template-rows: 1fr 1fr;
}
.calendar {
  display: block;
  background-image: url("./assets/confetti-pink.jpg");
  background-size: 110%;
}
.how-long {
  display: block;
  background-image: url("./assets/how-long.jpg");
  background-size: 100%;
}

/* 背景拉花 */
/* #confetti {
  margin: 0;
  padding: 0;
  z-index: 1;
} */
</style>
