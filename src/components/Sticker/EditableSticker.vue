<template>
  <div id='container'>
    <Sticker :name='name' :isLocked='isLocked' :class="isPreview ? 'preview' : ''"/>
    <Scissors v-if='isLocked' id='scissors'/>
  </div>
</template>

<script>
import Sticker from '@/components/Sticker/Sticker.vue'
import Scissors from '@/components/Sticker/Scissors.vue'

export default {
  name: 'EditableSticker',
  components: {
    Sticker,
    Scissors
  },
  props: [
    'name',
    'isLocked'
  ],
  data() {
    return {
      isPreview: false
    }
  },
  watch: {
    isLocked() {
      console.log('change');
      window.setTimeout(()=>{this.isPreview = true;}, 3000);
    }
  }
}
</script>

<style scoped>
#container {
  position: relative;
  margin: 35px;
}

#scissors {
  position: absolute;
  z-index: -1;
  top: 0;
  left: 0;
}

.preview {
  transition: transform 0.4s ease-in-out;
  transform: translate(-52px, 54px) scale(0.1);
}
</style>
