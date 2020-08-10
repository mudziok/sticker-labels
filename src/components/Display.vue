<template>
  <div id='display'>
    <div style="position: relative">
      <img src="../assets/toys.svg" class='toys' alt="Toys with stickers on them"/>
      <StaticSticker :name='selectedIcon' :text='text' :fontSize='fontSize' class='sticker s1'/>
      <StaticSticker :name='selectedIcon' :text='text' :fontSize='fontSize' class='sticker s2'/>
      <StaticSticker :name='selectedIcon' :text='text' :fontSize='fontSize' class='sticker s3'/>
    </div>
  </div>
</template>

<script>
import StaticSticker from '@/components/Sticker/StaticSticker.vue'

export default {
  name: 'Display',
  components: {
    StaticSticker
  },
  computed: {
    selectedIcon() {
      return this.$root.$children[0].selectedIcon;
    },
    text() {
      return this.$root.$children[0].text;
    },
    fontSize() {
      return this.$root.$children[0].fontSize;
    },
  }
}
</script>

<style scoped>
#display {
  width: 100%;
  height: 100%;
  
  position: absolute;
  top: 0;
  left: 0;

  z-index: -50;
  background-color: #5bcac0;

  display: flex;
  justify-content: center;
  align-items: center;
}

.toys {
  z-index: -10;
  position: relative;
  transform: scale(1) translateY(25%);
}

.sticker {
  transition: transform 0.4s ease-in-out;

  position: absolute;
  top: 0;
  left: 0;
}

.s1 {
  transform: translate(-120px, 50px) scale(0.125)
}
.s2 {
  transform: translate(67px, 35px) scale(0.125)
}
.s3 {
  transform: translate(111px, 86px) scale(0.125)
}

@media only screen and (min-width: 600px) {
  #display {
    transform: scale(1.3);
  }
}
</style>
