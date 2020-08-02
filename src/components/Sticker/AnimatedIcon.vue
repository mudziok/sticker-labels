<template>
  <div>
    <div class='icon' :class="isShrunk ? 'shrunk' : ''">
      <Icon :name='oldName'/>
    </div>
  </div>
</template>

<script>
import Icon from '@/components/Icon.vue'

export default {
  name: 'AnimatedIcon',
  components: {
    Icon
  },
  data() {
    return {
      oldName: '',
      isShrunk: true
    }
  },
  props: {
    name,
  },
  watch: {
    name() {
      this.isShrunk = true;
      window.setTimeout(() => {
        this.isShrunk = false;
        this.oldName = this.name;
      }, 200);
    }
  }
}
</script>

<style scoped>
.icon {
  transition: transform 0.2s cubic-bezier(.18,.89,.32,1.28);
}

.shrunk {
  transform: scale(0.3);
}
</style>
