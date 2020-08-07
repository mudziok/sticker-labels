<template>
  <div id='container' @click='focusTextInput()' ref='container'>
    <div id='wrapper' :style='wrapperStyle'>
      <textarea 
        class='font-style'
        v-model='text'
        @input='input'
        :style='textareaStyle'
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
      preloadedHeights: [],
      minFontSize: 21,
      textareaStyle: {
        'height' : '140px',
        'width' : '240px'
      },
      wrapperStyle: {
        'marginTop' : '0px'
      }
    }
  },
  mounted() {
    window.setTimeout(()=>{ this.preloadHeights(); }, 0); //TODO: this.preloadHeights has to be called after the font loads
  },
  methods: {
    preloadHeights() { //Finds the optimal font sizes for textarea beforehand to optimize the search alter
      let tests = ['|', '|\n|','|\n|\n|','|\n|\n|\n|','|\n|\n|\n|\n|','|\n|\n|\n|\n|\n|'];
      let f = 120; //short for font-size
      let i = 0;
      while (i < tests.length) { 
        while(this.getSizeOfText(tests[i], f).height >= 140) {
          f--;
        }
        this.preloadedHeights.push(f);
        i++; 
      }
    },
    input() {
      let minSize = this.getSizeOfText(this.text, this.minFontSize);
      if (minSize.width <= 200 && minSize.height <= 140 && this.preloadedHeights !== []) {
        this.previousText = this.text;
        this.positionText();
      }
      else {
        this.text = this.previousText;
      }
    },
    positionText() { //Finds the optimal font size and margin for textarea and applies it
      let fyi = 0; //Index for Font-size in the Y axis 
      while (this.getSizeOfText(this.text, this.preloadedHeights[fyi]).height >= 140) {
        fyi++;
      }
      let fx = this.preloadedHeights[fyi]; //Font-size in the X axis, always smalled than fy
      while (this.getSizeOfText(this.text, fx).width >= 200) {
        fx -= 1;
      }
      let f = Math.min(fx, this.preloadedHeights[fyi]);
      this.textareaStyle.fontSize = `${f}px`
      if (this.text == '') {
        this.wrapperStyle.marginTop = '0px';
      }
      else {
        let newHeight = this.getSizeOfText(this.text, f).height;
        this.wrapperStyle.marginTop = `${(140 - newHeight) / 2 }px`;
      }
      this.$root.$children[0].setText(this.text, f);
    },
    getSizeOfText(text, fontSize) { 
      let sampler = this.$refs.sampler;
      sampler.innerText = text.replace(/\n/g, "\n|");
      
      sampler.style.fontSize = `${fontSize}px`;
      let height = sampler.clientHeight;
      let width = sampler.clientWidth;

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
  height: 140px;
  transition: margin-top 0.2s ease-in-out;
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
  transition: font-size 0.2s ease-in-out;
  
  white-space: pre;
  overflow-wrap: normal;
}

#sampler { /* Hidden div that allows to calculate size of text in textbox */
  position: absolute;
  visibility: hidden;
  height: auto;
  width: auto;
  white-space: nowrap;
}

.font-style {
  font-family: 'Inter', sans-serif;
  font-size: 120px;
  text-align: center;
}
</style>
