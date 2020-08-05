<template>
  <div id='display'>
    <div style="position: relative">
      <img src="../assets/toys.svg" style='z-index: -10; position: relative' alt="Toys with stickers on them"/>
      <Sticker :name='selectedIcon' class='sticker s1'/>
      <Sticker :name='selectedIcon' class='sticker s2'/>
      <Sticker :name='selectedIcon' class='sticker s3'/>
    </div>
  </div>
</template>

<script>
import Sticker from '@/components/Sticker/Sticker.vue'

export default {
  name: 'Display',
  components: {
    Sticker
  },
  computed: {
    selectedIcon() {
      return this.$root.$children[0].selectedIcon;
    }
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
