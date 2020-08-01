<template>
  <div id='picker'>
    <div id="icon-container" class="shape" ref="container">
      <span style="font-size: 21px; margin: 0 0.5em">ANIMALS</span>
      <div class="icon">
        <Icon :name="'mouse'"/>
      </div>
      <div class="icon">
        <Icon :name="'cow'"/>
      </div>
    </div>
    <div id="shadow" class="shape"></div>
  </div>
</template>

<script>
import Icon from '@/components/Icon.vue'

export default {
  name: 'Picker',
  components: {
    Icon
  }
}
</script>

<style scoped>
#picker {
  margin: 35px 0;
  position: relative;
}

#icon-container {
  color: var(--accent);
  background: var(--primary);
  padding: 10px;
  font-size: 36px;

  display: flex;
  justify-content: flex-start;
  align-items: center;
}

.icon {
  width: 70px;
  height: 70px;
}

#shadow {
  position: absolute;
  transform: translateY(-24px);
  z-index: -1;
  height: 10px;
  padding: 10px;
  border-radius: 0 0 20px 20px;
  background: var(--accent);
}

.shape {
  min-width: 340px; 
  border-radius: 20px;
  overflow: hidden;
}
</style>
