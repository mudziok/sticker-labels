<template>
  <div id='display'>
    <div style="position: relative">
      <img src="../assets/toys.svg" style='z-index: -10; position: relative' alt="Toys with stickers on them"/>
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
  
  min-width: 430px;
  min-height: 300.5px;
  position: absolute;
  top: 0;
  left: 0;

  z-index: -50;
  background-color: #89c5ea;

  display: flex;
  justify-content: center;
  align-items: center;
}

.sticker {
  transition: transform 0.4s ease-in-out;

  position: absolute;
  top: 0;
  left: 0;
}

.s1 {
  transform: translate(-120px, -10px) scale(0.1);
}
.s2 {
  transform: translate(80px, 15px) scale(0.1);
}
.s3 {
  transform: translate(145px, 26px) scale(0.1);
}
</style>
