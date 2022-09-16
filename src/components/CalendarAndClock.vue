<script setup>
import { onMounted, ref } from "vue";

const monthNames = [
  "January",
  "February",
  "March",
  "April",
  "May",
  "June",
  "July",
  "August",
  "September",
  "October",
  "November",
  "December",
];
const dayNames = [
  "Sunday",
  "Monday",
  "Tuesday",
  "Wednesday",
  "Thursday",
  "Friday",
  "Saturday",
];
const day = ref("Monday");
const date = ref("1");
const month = ref("January");
const year = ref("2022");
const hour = ref("");
const minute = ref("");
const second = ref("");

function getTime(nowDate) {
  const newDate = new Date(nowDate);
  day.value = dayNames[newDate.getDay()];
  month.value = monthNames[newDate.getMonth()];
  year.value = newDate.getFullYear();
  date.value = newDate.getDate();
  hour.value = (newDate.getHours() < 10 ? "0" : "") + newDate.getHours();
  minute.value = (newDate.getMinutes() < 10 ? "0" : "") + newDate.getMinutes();
  second.value = (newDate.getSeconds() < 10 ? "0" : "") + newDate.getSeconds();
}
onMounted(() => {
  // 每秒刷新
  setInterval(() => {
    getTime(new Date());
  }, 1000);
});
</script>
<template>
  <div class="calendar-and-clock"></div>
  <div class="info anim04c"></div>

  <!-- main codes start -->
  <div class="signboard outer">
    <div class="signboard front inner anim04c">
      <li class="year anim04c">
        <span>{{ year }}</span>
      </li>
      <ul class="calendarMain anim04c">
        <li class="month anim04c">
          <span>{{ month }}</span>
        </li>
        <li class="date anim04c">
          <span>{{ date }}</span>
        </li>
        <li class="day anim04c">
          <span>{{ day }}</span>
        </li>
      </ul>
      <li class="clock minute anim04c">
        <span>{{ minute }}</span>
      </li>
      <li class="calendarNormal date2 anim04c">
        <span>{{ date }}</span>
      </li>
    </div>
    <div class="signboard left inner anim04c">
      <li class="clock hour anim04c">
        <span>{{ hour }}</span>
      </li>
      <li class="calendarNormal day2 anim04c">
        <span>{{ day }}</span>
      </li>
    </div>
    <div class="signboard right inner anim04c">
      <li class="clock second anim04c">
        <span>{{ second }}</span>
      </li>
      <li class="calendarNormal month2 anim04c">
        <span>{{ month }}</span>
      </li>
    </div>
  </div>
  <!-- main codes end -->
  
</template>
<style scoped>
/* -- usable codes start -- */

span,
object,
iframe,
h1,
h2,
h3,
h4,
h5,
h6,
p,
blockquote,
pre,
a,
abbr,
acronym,
address,
code,
del,
dfn,
em,
img,
q,
dl,
dt,
dd,
ol,
ul,
li,
fieldset,
form,
label,
legend,
table,
caption,
tbody,
tfoot,
thead,
tr,
th,
td,
article,
aside,
dialog,
figure,
footer,
header,
hgroup,
nav,
section {
  margin: 0;
  padding: 0;
  border: 0;
  font-weight: inherit;
  font-style: inherit;
  font-size: 100%;
  font-family: "Source Sans Pro", sans-serif;
  vertical-align: baseline;
  text-decoration: none;
  list-style: none;
}
img {
  width: 100%;
}
.anim04c {
  -webkit-transition: all 0.4s cubic-bezier(0.5, 0.35, 0.15, 1.4);
  transition: all 0.4s cubic-bezier(0.5, 0.35, 0.15, 1.4);
}

/*-----*/

.outer {
  position: relative;
  top: 50%;
  z-index: 1;
  -webkit-transform: translateY(-50%);
  -moz-transform: translateY(-50%);
  -ms-transform: translateY(-50%);
  -o-transform: translateY(-50%);
  transform: translateY(-50%);
  cursor: pointer;
}
/*-----*/

.signboard {
  width: 100px;
  height: 100px;
  margin: auto;
  color: #fff;
  border-radius: 10px;
}
/*-----*/

.front {
  position: absolute;
  top: 0;
  left: 0;
  z-index: 3;
  background: #ff726b;
  text-align: center;
}
.right {
  position: absolute;
  right: 0;
  z-index: 2;
  -webkit-transform: rotate(-10deg) translate(7px, 8px);
  -moz-transform: rotate(-10deg) translate(7px, 8px);
  -ms-transform: rotate(-10deg) translate(7px, 8px);
  -o-transform: rotate(-10deg) translate(7px, 8px);
  transform: rotate(-10deg) translate(7px, 8px);
  background: #efc94c;
}
.left {
  position: absolute;
  left: 0;
  z-index: 1;
  -webkit-transform: rotate(5deg) translate(-4px, 4px);
  -moz-transform: rotate(5deg) translate(-4px, 4px);
  -ms-transform: rotate(5deg) translate(-4px, 4px);
  -o-transform: rotate(5deg) translate(-4px, 4px);
  transform: rotate(5deg) translate(-4px, 4px);
  background: #3498db;
}
/*-----*/

.outer:hover .inner {
  -webkit-transform: rotate(0) translate(0);
  -moz-transform: rotate(0) translate(0);
  -ms-transform: rotate(0) translate(0);
  -o-transform: rotate(0) translate(0);
  transform: rotate(0) translate(0);
}
/*-----*/

.outer:active .inner {
  -webkit-transform: rotate(0) translate(0) scale(0.9);
  -moz-transform: rotate(0) translate(0) scale(0.9);
  -ms-transform: rotate(0) translate(0) scale(0.9);
  -o-transform: rotate(0) translate(0) scale(0.9);
  transform: rotate(0) translate(0) scale(0.9);
}
.outer:active .front .date {
  -webkit-transform: scale(2);
}
.outer:active .front .day,
.outer:active .front .month {
  visibility: hidden;
  opacity: 0;
  -webkit-transform: scale(0);
  -moz-transform: scale(0);
  -ms-transform: scale(0);
  -o-transform: scale(0);
  transform: scale(0);
}
.outer:active .right {
  -webkit-transform: rotate(-5deg) translateX(80px) scale(0.9);
  -moz-transform: rotate(-5deg) translateX(80px) scale(0.9);
  -ms-transform: rotate(-5deg) translateX(80px) scale(0.9);
  -o-transform: rotate(-5deg) translateX(80px) scale(0.9);
  transform: rotate(-5deg) translateX(80px) scale(0.9);
}
.outer:active .left {
  -webkit-transform: rotate(5deg) translateX(-80px) scale(0.9);
  -moz-transform: rotate(5deg) translateX(-80px) scale(0.9);
  -ms-transform: rotate(5deg) translateX(-80px) scale(0.9);
  -o-transform: rotate(5deg) translateX(-80px) scale(0.9);
  transform: rotate(5deg) translateX(-80px) scale(0.9);
}
/*-----*/

.outer:active .calendarMain {
  -webkit-transform: scale(1.8);
  opacity: 0;
  visibility: hidden;
}
.outer:active .clock {
  -webkit-transform: scale(1.4);
  opacity: 1;
  visibility: visible;
}
.outer:active .calendarNormal {
  bottom: -30px;
  opacity: 1;
  visibility: visible;
}
.outer:active .year {
  top: -30px;
  opacity: 1;
  visibility: visible;
  letter-spacing: 3px;
}
/*-----*/

.calendarMain {
  width: 100%;
  height: 100%;
  position: absolute;
  opacity: 1;
}
.month,
.day {
  font-size: 10px;
  line-height: 30px;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 3px;
}
.date {
  font-size: 40px;
  line-height: 40px;
  font-weight: 300;
  text-transform: uppercase;
  letter-spacing: 3px;
}
/*-----*/

.clock {
  width: 100%;
  height: 100%;
  position: absolute;
  font-size: 40px;
  line-height: 100px;
  font-weight: 300;
  text-transform: uppercase;
  letter-spacing: 3px;
  text-align: center;
  opacity: 0;
  visibility: hidden;
}
/*-----*/

.year {
  width: 100%;
  position: absolute;
  top: 0;
  font-size: 14px;
  line-height: 30px;
  font-weight: 300;
  text-transform: uppercase;
  letter-spacing: 0;
  text-align: center;
  opacity: 0;
  visibility: hidden;
  color: #ff726b;
}
.calendarNormal {
  width: 100%;
  position: absolute;
  bottom: 0;
  font-size: 14px;
  line-height: 30px;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 3px;
  text-align: center;
  opacity: 0;
  visibility: hidden;
}
.date2 {
  color: #ff726b;
}
.day2 {
  color: #3498db;
}
.month2 {
  color: #efc94c;
}
/* -- usable codes end -- */

/* -- unusable codes (text, logo, etc.) -- */

.info {
  width: 100%;
  height: 25%;
  position: absolute;
  top: 15%;
  text-align: center;
  opacity: 0;
}
.info li {
  width: 100%;
}
.hover,
.click,
.yeaa {
  font-size: 14px;
  line-height: 25px;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 2px;
  text-align: center;
  bottom: 0;
  opacity: 1;
}
em {
  color: #ed4988;
}
.designer {
  width: 100%;
  height: 50%;
  position: absolute;
  bottom: 0;
  text-align: center;
  opacity: 0;
}
.designer li {
  width: 100%;
  position: absolute;
  bottom: 30%;
}
.designer a {
  width: 30px;
  height: 30px;
  display: block;
  position: relative;
  border-radius: 100%;
  margin: auto;
  color: rgba(46, 204, 113, 0.55);
}
.designer a:after {
  content: "see designs";
  position: absolute;
  top: 0;
  left: 40px;
  font-size: 14px;
  line-height: 33px;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 2px;
  white-space: nowrap;
}
.designer a:hover:after {
  color: #2ecc71;
}
.designer img {
  display: block;
  border-radius: 100%;
}
.calendar-and-clock:hover .info,
.calendar-and-clock:hover .designer {
  opacity: 1;
}
::selection {
  background: transparent;
}
::-moz-selection {
  background: transparent;
}


</style>
