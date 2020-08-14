<template>
  <div id='picker' class='shape'>
    <div id='columns' :style='columnsStyle'>
      <div id="category-container" ref="container">
        <Category 
          v-for="(category, index) in categories.entries"
          :key="index"
          :name="category.name"
          :icons="category.icons" />
      </div>
      <div id="category-container" ref="container">
        
      </div>
    </div>
    <div id="shadow" class="shape"></div>
  </div>
</template>

<script>
import Category from '@/components/Picker/Category.vue'
import CATEGORIES_JSON from '@/assets/categories.json'

export default {
  name: 'Picker',
  components: {
    Category
  },
  props: [
    'appState'
  ],
  data() {
    return {
      categories: CATEGORIES_JSON,
    }
  },
  computed: {
    columnsStyle() {
      let x = this.appState * 50;
      return {
        'transform' : `translateX(-${x}%)`
      }
    }
  }
}
</script>

<style scoped>
#picker {
  position: relative;
  width: 100%;
  max-width: 600px;
}

#category-container {
  color: var(--accent);
  background: var(--primary);
  font-size: 36px;
  width: 100%;

  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: center;
}

#category-container div:nth-child(2n) {
  background: #ecfbf8;
}

#columns {
  width: 200%;
  display: flex;

  transition: all 1.2s ease-in-out;
  transition-delay: 2.3s;
}

.icon {
  width: 70px;
  height: 70px;
}

#shadow {
  position: absolute;
  width: 100%;
  transform: translateY(-14px);
  z-index: -1;
  height: 20px;
  padding: 0;
  border-radius: 0 0 20px 20px;
  background: var(--accent);
}

.shape {
  border-radius: 20px;
  overflow: hidden;
}

</style>
