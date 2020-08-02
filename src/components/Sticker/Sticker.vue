<template>
  <div id='sticker'>
    <div id='icon-container' class='both'>
      <AnimatedIcon :name='name' style='font-size: 55px' />
    </div>
    <div id='text-container' class='both'>
      <TextInput />
    </div>
    <Scissors v-if='isLocked' id='scissors'/>
    <div id='shadow'>
      <div id='icon-container' class='both'></div>
      <div id='text-container' class='both'></div>
    </div>
  </div>
</template>

<script>
import TextInput from '@/components/Sticker/TextInput.vue'
import AnimatedIcon from '@/components/Sticker/AnimatedIcon.vue'
import Scissors from '@/components/Sticker/Scissors.vue'

export default {
  name: 'Sticker',
  components: {
    TextInput,
    AnimatedIcon,
    Scissors
  },
  props: [
    'name',
    'isLocked'
  ],
  watch: {
    isLocked() {
      console.log('change');
    }
  }
}
</script>

<style scoped>
#sticker {
  display: flex;
  justify-content: flex-start;
  align-items: center;
  position: relative;
  
  margin: 35px;
}

#shadow {
  display: flex;
  justify-content: flex-start;
  align-items: center;

  position: absolute;
  transform: translateY(6px);
  z-index: -2;
}

#icon-container {
  width: 100px;  
  border-radius: 70px 0 0 70px; /* TL BL rounded*/
  padding-left: 20px;

  display: flex;
  justify-content: center;
  align-items: center;
}

#text-container {
  width: 240px;  
  border-radius: 0 20px 20px 0; /* TR BR rounded*/
  overflow: hidden;
}

.both {
  height: 140px;
  background: var(--primary);
  color: var(--accent);
}

#shadow .both {
  background: var(--accent);
}

#scissors {
  position: absolute;
  z-index: -1;
  top: 0;
  left: 0;
}
</style>
