<template>
  <div>
    <div id="scissor1" class="settings">
      <img src="@/assets/scissors.png" class="settings">
    </div>
  </div>
</template>

<script>
export default {
  name: 'Scissors'
}
</script>

<style scoped>
div > div{
  width: 80px;
  transform: translate(-80px, 0px);
  height: 37px;
  transform-origin: center;
}

img {
  width: 100%;
  opacity: 0;
}

#scissor1 {
  animation-name: anchor-anim;
}

#scissor1 img {
  animation-name: img-anim, img-clip, img-opacity;
}

.settings {
  animation-iteration-count: 1;
  animation-duration: 3s;
  animation-timing-function: ease-in-out;
  transform-origin: center;
}

@keyframes img-anim {
  0% { transform: rotate(0deg) translate(0px, -20px); }
  25% { transform: rotate(0deg) translate(0px, -20px); }
  30% { transform: rotate(90deg) translate(0px, -20px); }
  45% { transform: rotate(90deg) translate(0px, -20px); }
  50% { transform: rotate(180deg) translate(0px, -20px); }
  75% { transform: rotate(180deg) translate(0px, -70px); }
  100% { transform: rotate(360deg) translate(0px, -70px);  }
}

@keyframes img-clip {
  0% { clip-path: none; }
  24% { clip-path: polygon(0 0, 100% 0, 100% 60%, 0 60%); }
  100% { clip-path: polygon(0 0, 100% 0, 100% 60%, 0 60%); }
}

@keyframes img-opacity {
  0% { opacity: 0; }
  8% { opacity: 1; }
  92% { opacity: 1; }
  100% { opacity: 0; }
}

@keyframes anchor-anim {
  0% { transform: translate(0px, -17px); }
  25% {transform: translate(380px, -17px); }
  30% {transform: translate(380px, -17px); }
  45% {transform: translate(380px,  83px); }
  50% {transform: translate(380px,  83px); }
  75% {transform: translate(110px,  33px); }
  100% {transform: translate(110px, 33px);}
}
</style>
