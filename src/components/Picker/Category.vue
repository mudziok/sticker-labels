<template>
  <div id='category'>
    <div class='label'>
      <span>{{name.toUpperCase()}}</span>
    </div>
    <div class="icon" v-for="(icon, index) in icons" :key="index">
      <SelectableIcon :name="icon"/>
    </div>
  </div>
</template>

<script>
import SelectableIcon from '@/components/Picker/SelectableIcon.vue'

export default {
  name: 'Category',
  props: [
    'name',
    'icons'
  ],
  components: {
    SelectableIcon
  }
}
</script>

<style scoped>
#category {
  font-size: 36px;
  padding: 10px;
  width: calc(100% - 20px);

  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(72px, 1fr));
}

.label {
  font-size: 19px;
  text-align: left;
  padding-left: 10px;
  grid-column: 1 / span 2;

  display: flex;
  justify-content: flex-start;
  align-items: center;
}

.icon {
  width: 2em;
  height: 2em;

  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
