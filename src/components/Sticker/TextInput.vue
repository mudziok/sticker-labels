<template>
  <div id='text-input'>
    <textarea class="font-style" v-model="text" @input="input"/>
    <div id='sampler' ref="sampler" class="font-style"></div>
  </div>
</template>

<script>
export default {
  name: 'TextInput',
  data() {
    return {
      text: '',
      previousText: ''
    }
  },
  methods: {
    input() {
      if (this.getSizeOfText(this.text).width > 195) {
        this.text = this.previousText;
      }
      else this.previousText = this.text;
    },
    getSizeOfText(text) { 
      let sampler = this.$refs.sampler;
      sampler.innerText = text;

      let height = sampler.clientHeight;
      let width = sampler.clientWidth;

      return {
        'height': height, 
        'width': width
      }
    }
  }
}
</script>

<style scoped>
#text-input {
  color: var(--accent);
}

textarea {
  width: 200px;
  height: 140px;
  padding: 0;
  margin: 0;
  border: none;

  resize: none;
  overflow: hidden;
}

#sampler { /* Hidden div that allows to calculate size of text in textbox */
  position: absolute;
  visibility: hidden;
  height: auto;
  width: auto;
  white-space: nowrap;
}

.font-style {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  font-size: 24px;
  text-align: center;
}
</style>
