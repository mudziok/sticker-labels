<template>
  <div id='container' @click='focusTextInput()' ref='container'>
    <div id='wrapper' v-bind:style='wrapperStyle'>
      <textarea 
        class='font-style'
        v-model='text' 
        @input='input'
        v-bind:style='textareaStyle'
        spellcheck='false'
        ref='textarea' />
    </div>
    <div id='sampler' ref='sampler' class='font-style'></div>
  </div>
</template>

<script>
export default {
  name: 'TextInput',
  data() {
    return {
      text: '',
      previousText: '',
      transform: {
        y: 70,
        scale: 1
      },
      width: 200,
      height: 140,
      textareaStyle: {
        'transform': 'scale(5)',
        'height' : '28px',
        'width' : '40px'
      },
      wrapperStyle: {
        'height' : '140px',
        'transfrom' : 'translateY(0px)'
      }
    }
  },
  mounted() {
    this.width = this.$refs.container.clientWidth;
    this.height = this.$refs.container.clientHeight;
  },
  methods: {
    input() {
      let size = this.getSizeOfText(this.text);

      if (size.width > this.width - 6) {
        this.text = this.previousText;
      }
      else if (size.height > this.height) {
        this.text = this.previousText;
      }
      else {
        this.previousText = this.text;

        let scaleY = this.height / size.height;
        let scaleX = this.width / (size.width + 6);
        let scale = Math.min(scaleX, scaleY);

        this.textareaStyle.height = `${size.height}px`;
        this.textareaStyle.width = `${size.width + 6}px`;
        this.textareaStyle.transform = `scale(${scale})`;

        this.wrapperStyle.height = `${size.height * scale}px`;
        this.wrapperStyle.transform = `translateY(${(this.height - (size.height * scale)) / 2}px)`;
      }
    },
    getSizeOfText(text) { 
      let sampler = this.$refs.sampler;
      sampler.innerText = text.replace(/\n/g, "\n|");

      let height = sampler.clientHeight;
      let width = sampler.clientWidth;
      if (height < 28) { height = 28; }

      return {
        'height': height, 
        'width': width
      }
    },
    focusTextInput() {
      this.$refs.textarea.focus();
    }
  }
}
</script>

<style scoped>
#container {
  color: var(--accent);
  cursor: text;
}

#wrapper {
  width: 100%;
  transition: transform 0.2s ease-in-out;
}

textarea {
  padding: 0;
  margin: 0;

  resize: none;
  overflow: hidden;
  transform-origin: center top;
  outline: none;

  color: var(--accent);
  caret-color: var(--accent);
  background: transparent;
  border: none;
  -webkit-appearance: none;
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
