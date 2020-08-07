<template>
  <div id="app">
    <h1>Sticker Creator</h1>
    <div id='hero'>
      <Display/>
      <EditableSticker :name='selectedIcon' :isLocked='isLocked'/>
      <a @click="isLocked = true">
        <Button style="font-size: 21px">Get this sticker!</Button>
      </a>
    </div>
    <Picker />
  </div>
</template>

<script>
import EditableSticker from '@/components/Sticker/EditableSticker.vue'
import Button from '@/components/Button.vue'
import Display from '@/components/Display.vue'
import Picker from '@/components/Picker/Picker.vue'

export default {
  name: 'App',
  components: {
    EditableSticker,
    Button,
    Picker,
    Display
  },
  data() {
    return {
      selectedIcon: '',
      text: '',
      fontSize: 120,
      isLocked: false
    }
  },
  methods: {
    selectIcon(name) {
      this.selectedIcon = name;
    },
    setText(text, fontSize) {
      this.text = text;
      this.fontSize = fontSize;
    },
  }
}
</script>

<style>
:root {
  --background: #64dbd1;
  --primary: #f0fffc;
  --accent: #2f596d;
}

#hero {
  min-width: 430px;
  min-height: 300.5px;

  position: relative;
}

a {
  -webkit-tap-highlight-color: transparent;
}

body {
  background: var(--background);
  overflow-x: hidden;
  overflow-y: scroll;
}

#app {
  font-family: 'Inter', sans-serif;
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
