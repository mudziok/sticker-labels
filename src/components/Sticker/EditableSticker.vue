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
      window.setTimeout(()=>{this.isPreview = true;}, 3200);
    }
  }
}
</script>

<style scoped>
#container {
  position: relative;
  margin: 35px auto;
  width: max-content;
}

#scissors {
  position: absolute;
  z-index: -1;
  top: 0;
  left: 0;
}

.preview {
  transition: transform 0.4s ease-in-out;
  transform: translate(-46px, 74px) scale(0.125);
}

@media only screen and (min-width: 600px) {
  .preview {
    transform: translate(-58px, 84px) scale(0.1625);
  }
}
</style>
