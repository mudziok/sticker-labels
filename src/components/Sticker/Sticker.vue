<template>
  <div id='sticker'>
    <div id='icon-container' class='both'>

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

export default {
  name: 'Sticker',
  components: {
    TextInput
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
  width: 140px;  
  border-radius: 50% 0 0 50%; /* TL BL rounded*/
}

#text-container {
  width: 200px;  
  border-radius: 0 20px 20px 0; /* TR BR rounded*/
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
