<template>
  <div id="app">
    <h1>Sticker Creator</h1>
    <div id='hero'>
      <Display/>
      <img src="./assets/outline.svg" class='background' :class="isLocked ? 'locked' : ''" alt="Sticker outline"/>
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
  width: 100%;
  overflow: hidden;
  position: relative;
  margin: 10px 0;
}

a {
  -webkit-tap-highlight-color: transparent;
}

.background {
  position: absolute;
  top: 35px;
  left: calc(50% - 180px);
  box-shadow: 0px 0px 0px 1000px var(--background);
  z-index: -5;
  transition: all 0.5s ease-in;
  transform-origin: center;
  transition-delay: 2.5s;
}

.background.locked {
  transform: scale(1.25);
  opacity: 0;
}

body {
  background: var(--background);
  overflow-x: hidden;
  overflow-y: scroll;
  margin: 0;
  padding: 0;
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
