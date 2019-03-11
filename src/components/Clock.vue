<template>
  <div class="experiment">
    <div class="wrapper">
      <div id="experiment">
        <div id="clock">
          <div id="hour">
            <img id="hourHand" />
          </div>
          <div id="minute">
            <img id="minuteHand" />
          </div>
          <div id="second">
            <img id="secondHand" />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
//var $ = global.jQuery;
import $ from "jquery";
import clockFace from "../../public/clockFace.png";
import hourHand from "../../public/hourHand.png";
import minuteHand from "../../public/minuteHand.png";
import secondHand from "../../public/secondHand.png";

//window.addEventListener("load", function() {
// eslint-disable-next-line no-unused-vars
function clockready() {
  document.getElementById("hourHand").src = hourHand;
  document.getElementById("minuteHand").src = minuteHand;
  document.getElementById("secondHand").src = secondHand;
  document.getElementById("clock").style.backgroundImage = clockFace;
  var props = "transform WebkitTransform MozTransform OTransform msTransform".split(
    " "
  );
  var prop;
  var el = document.createElement("div");

  for (var i = 0, l = props.length; i < l; i++) {
    if (typeof el.style[props[i]] !== "undefined") {
      prop = props[i];
      break;
    }
  }

  function startClock() {
    var angle = 360 / 60,
      date = new Date(),
      hour = date.getHours() % 12,
      minute = date.getMinutes(),
      second = date.getSeconds(),
      hourAngle = (360 / 12) * hour + (360 / (12 * 60)) * minute;

    if (prop) {
      $("#minute")[0].style[prop] = "rotate(" + angle * minute + "deg)";
      $("#second")[0].style[prop] = "rotate(" + angle * second + "deg)";
      $("#hour")[0].style[prop] = "rotate(" + hourAngle + "deg)";
    }
  }
  setInterval(startClock, 1);
}
export default {
  name: "Clock",
  props: {
    msg: String
  },
  mounted() {
    clockready();
    // eslint-disable-next-line no-console
    console.log("MOUNT TEMPLATES");
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.start {
  text-align: center;
  font-size: 2em;
  font-weight: bold;
  margin: 0 0 2em;
}

#clock {
  position: relative;
  width: 378px;
  height: 378px;
  background-image: url("../../public/clockFace.png");
  margin: 3em auto;
}

#clock div {
  position: absolute;
}

/* The magic */
#clock img[src*="second"] {
  -webkit-transition: -webkit-transform 600000s linear;
  -moz-transition: -moz-transform 600000s linear;
  -o-transition: -o-transform 600000s linear;
  -ms-transition: -ms-transform 600000s linear;
  transition: transform 600000s linear;
}

#clock img[src*="second"] {
  -webkit-transform: rotate(3600000deg);
  -moz-transform: rotate(3600000deg);
  -o-transform: rotate(3600000deg);
  -ms-transform: rotate(3600000deg);
  transform: rotate(3600000deg);
}

#clock img[src*="minute"] {
  -webkit-transition: -webkit-transform 360000s linear;
  -moz-transition: -moz-transform 360000s linear;
  -o-transition: -o-transform 360000s linear;
  -ms-transition: -ms-transform 360000s linear;
  transition: transform 360000s linear;
}

#clock img[src*="minute"] {
  -webkit-transform: rotate(36000deg);
  -moz-transform: rotate(36000deg);
  -o-transform: rotate(36000deg);
  -ms-transform: rotate(36000deg);
  transform: rotate(36000deg);
}

#clock img[src*="hour"] {
  -webkit-transition: -webkit-transform 216000s linear;
  -moz-transition: -moz-transform 216000s linear;
  -o-transition: -o-transform 216000s linear;
  -ms-transition: -ms-transform 216000s linear;
  transition: transform 216000s linear;
}

#clock img[src*="hour"] {
  -webkit-transform: rotate(360deg);
  -moz-transform: rotate(360deg);
  -o-transform: rotate(360deg);
  -ms-transform: rotate(360deg);
  transform: rotate(360deg);
}
</style>
