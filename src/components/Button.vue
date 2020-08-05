<template>
  <div class="button">
    <div class="body" ontouchstart="">
      <slot />
    </div>
    <div class="shadow"></div>
  </div>
</template>

<script>
export default {
  name: 'Button',
  props: {
    name,
  }
}
</script>

<style scoped>
.button {
  margin: 35px;
  position: relative;
}

.body {
  padding: 0.75em 1.5em;

  background: #c6e9e5;
  color: var(--accent);
  border-radius: 20px;
  cursor: pointer;
  transition: all 0.1s ease-in-out;

  user-select: none; 
}

.body:active {
  transform: translateY(6px);
}

.shadow {
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  height: 40px;
  z-index: -2;

  background: var(--accent);
  border-radius: 0 0 20px 20px;
  transform: translateY(6px);
}
</style>
