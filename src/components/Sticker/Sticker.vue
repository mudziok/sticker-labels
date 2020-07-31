<template>
  <div id='sticker'>
    <div id='icon-container' class='both'>

    </div>
    <div id='text-container' class='both'>
      
    </div>
    <div id='shadow'>
      <div id='icon-container' class='both'></div>
      <div id='text-container' class='both'></div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Sticker',
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
  transform: translate(0, 6px);
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
