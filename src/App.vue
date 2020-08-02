<template>
  <div id="app">
    <h1>Sticker Creator</h1>
    <Sticker :name='selectedIcon' :isLocked='isLocked'/>
    <a @click="isLocked = true">
      <Button style="font-size: 21px">Get this sticker!</Button>
    </a>
    <Picker />
  </div>
</template>

<script>
import Sticker from '@/components/Sticker/Sticker.vue'
import Button from '@/components/Button.vue'
import Picker from '@/components/Picker/Picker.vue'

export default {
  name: 'App',
  components: {
    Sticker,
    Button,
    Picker
  },
  data() {
    return {
      selectedIcon: '',
      isLocked: false
    }
  },
  methods: {
    selectIcon(name) {
      this.selectedIcon = name;
    }
  }
}
</script>

<style>
:root {
  --background: #64dbd1;
  --primary: #f0fffc;
  --accent: #2f596d;
}

a {
  -webkit-tap-highlight-color: transparent;
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
