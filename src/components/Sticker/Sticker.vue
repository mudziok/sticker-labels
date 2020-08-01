<template>
  <div id='sticker'>
    <div id='icon-container' class='both'>
      <Icon :name='this.$root.$children[0].selectedIcon' style='font-size: 55px' />
    </div>
    <div id='text-container' class='both'>
      <TextInput />
    </div>
    <div id='shadow'>
      <div id='icon-container' class='both'></div>
      <div id='text-container' class='both'></div>
    </div>
  </div>
</template>

<script>
import TextInput from '@/components/Sticker/TextInput.vue'
import Icon from '@/components/Icon.vue'

export default {
  name: 'Sticker',
  components: {
    TextInput,
    Icon
  }
}
</script>

<style scoped>
#sticker {
  display: flex;
  justify-content: flex-start;
  align-items: center;
  position: relative;
  
}

#shadow {
  display: flex;
  justify-content: flex-start;
  align-items: center;

  position: absolute;
  transform: translateY(6px);
  z-index: -1;
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
</style>
