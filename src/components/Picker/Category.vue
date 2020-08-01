<template>
  <div id='category'>
    <span style="font-size: 19px; margin: 0 0.5em">{{name.toUpperCase()}}</span>
    <div class="icon" v-for="(icon, index) in icons" :key="index">
      <Icon :name="icon"/>
    </div>
  </div>
</template>

<script>
import Icon from '@/components/Icon.vue'

export default {
  name: 'Category',
  props: [
    'name',
    'icons'
  ],
  components: {
    Icon
  }
}
</script>

<style scoped>
#category {
  color: var(--accent);
  background: var(--primary);
  padding: 10px;
  font-size: 36px;
  width: 100%;

  display: flex;
  justify-content: flex-start;
  align-items: center;
  flex-wrap: wrap;
}

.icon {
  width: 2em;
  height: 2em;
}
</style>
