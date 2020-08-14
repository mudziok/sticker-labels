<template>
  <a class="selection" @click="choose(name)" :class="this.selected ? 'active' : ''"> 
      <Icon :name='name' class="icon"/>
  </a>
</template>

<script>
import Icon from '@/components/Icon.vue'

export default {
  name: 'SelectableIcon',
  components: {
    Icon
  },
  props: {
    name,
  },
  methods: {
    choose(name) {
      this.$root.$children[0].selectIcon(name);
    }
  },
  computed: {
    selected() {
      return this.$root.$children[0].icon === this.name ? true : false;
    }
  }
}
</script>

<style scoped>
.selection {
  width: 95%;
  height: 95%;

  border-radius: 50%;
  cursor: pointer;
  -webkit-tap-highlight-color: transparent;

  display: flex;
  justify-content: center;
  align-items: center;

  transition: background-color 0.1s ease-out;
}

.selection.active {
  background: #c6e9e5;
}

.icon {
  transition: transform 0.1s ease-in-out;
}

.icon:hover {
  transform: scale(1.1);
}

.icon:active {
  transform: scale(1);
}
</style>
