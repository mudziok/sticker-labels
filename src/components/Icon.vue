<template>
  <i :class='`flaticon-${name}`' v-if="name !== ''"></i>
</template>

<script>
export default {
  name: 'Icon',
  props: {
    name,
  }
}
</script>

<style scoped>
#container {
  width: 100%;
  height: 100%;
  
  display: flex;
  justify-content: center;
  align-items: center;
}

i::before {
  margin: 0;
  font-size: 1.5em; 
}
</style>
