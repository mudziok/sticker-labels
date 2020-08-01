<template>
  <div id="app">
    <h1>Sticker Creator</h1>
    <Sticker />
    <Picker />
  </div>
</template>

<script>
import Sticker from '@/components/Sticker/Sticker.vue'
import Picker from '@/components/Picker/Picker.vue'

export default {
  name: 'App',
  components: {
    Sticker,
    Picker
  }
}
</script>

<style>
:root {
  --background: #64dbd1;
  --primary: #f0fffc;
  --accent: #2f596d;
}

body {
  background: var(--background);
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;

  text-align: center;
  color: var(--primary);
  margin-top: 60px;

  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: center;
}

h1 {
  font-size: 56px;
}
</style>
