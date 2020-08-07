<template>
  <div id='sticker' :class="isLocked ? 'isLocked' : ''" ref="sticker">
    <div id='icon-container' class='both'>
      <AnimatedIcon :name='name' style='font-size: 55px' />
    </div>
    <div id='text-container' class='both' :style="`font-size: ${fontSize}px`">
      {{text}}
    </div>
    <div id='shadow'>
      <div id='icon-container' class='both'></div>
      <div id='text-container' class='both'></div>
    </div>
  </div>
</template>

<script>
import AnimatedIcon from '@/components/Sticker/AnimatedIcon.vue'

export default {
  name: 'Sticker',
  components: {
    AnimatedIcon
  },
  props: {
    name: String,
    text: String,
    fontSize: Number,
    isLocked: {
      default: true
    }
  }
}
</script>

<style scoped>
#sticker {
  display: flex;
  justify-content: flex-start;
  align-items: center;
  
}

.isLocked {
  pointer-events: none;
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

  display: flex;
  justify-content: center;
  align-items: center;

  font-size: 20px;
}

.both {
  height: 140px;
  background: var(--primary);
  color: var(--accent);
}

#shadow .both {
  background: var(--accent);
}
</style>
