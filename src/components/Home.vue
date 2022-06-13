<template>
  <div class="home">
    <label>
      <input type="radio" name="comp" @change="activeSection = 'comp1'" checked>
      comp1
    </label>
    <label>
      <input type="radio" name="comp" @change="activeSection = 'comp2'">
      comp2
    </label>

    <div class="wrapper">
      <transition name="section">
        <component :is="activeSection"></component>
      </transition>
    </div>
  </div>
</template>

<script>
import comp1 from './comp1';
import comp2 from './comp2';

export default {
  components: {
    comp1,
    comp2
  },
  data() {
    return {
      activeSection: 'comp1'
    }
  }
}
</script>

<style scoped>
.wrapper {
  position: relative;
  overflow: hidden;
  height: 300px;
  width: 100vw;
}
.wrapper > * {
  position: absolute;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
  transform: translate3d(0,0,0);
}

.section-leave-active,
.section-enter-active {
  transition: all 10s;
}
.section-enter {
  top: 100%;
}
.section-leave-to {
  top: -100%;
}
</style>
