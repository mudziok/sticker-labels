<template>
  <div id='picker'>
    <div id="category-container" class="shape" ref="container" :class="isCollapsed ? 'collapsed' : ''">
      <Category 
        v-for="(category, index) in categories.entries"
        :key="index"
        :name="category.name"
        :icons="category.icons" />
    </div>
    <div id="shadow" class="shape" :class="isCollapsed ? 'collapsed' : ''"></div>
  </div>
</template>

<script>
import Category from '@/components/Picker/Category.vue'
import categories_json from '@/assets/categories.json'

export default {
  name: 'Picker',
  components: {
    Category
  },
  props: [
    'isCollapsed'
  ],
  data() {
    return {
      categories: categories_json
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

  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: center;
}

#category-container div:nth-child(2n) {
  background: #ecfbf8;
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
  transition: all 1s ease-in-out;
  transition-delay: 0.2s;
  max-height: 1000px;
}

</style>
