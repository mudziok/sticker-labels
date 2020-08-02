<template>
  <div id='picker'>
    <div id="category-container" class="shape" ref="container">
      <Category 
        :name="'Animals'"
        :icons="['mouse','cow','kangaroo','bear','flamingo','fox','bat','crab','lion']"/>
    </div>
    <div id="shadow" class="shape"></div>
  </div>
</template>

<script>
import Category from '@/components/Picker/Category.vue'

export default {
  name: 'Picker',
  components: {
    Category
  }
}
</script>

<style scoped>
#picker {
  margin: 35px 0;
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
  width: calc(100% - 20px);
  transform: translateY(-24px);
  z-index: -1;
  height: 10px;
  padding: 10px;
  border-radius: 0 0 20px 20px;
  background: var(--accent);
}

.shape {
  border-radius: 20px;
  overflow: hidden;
}
</style>
