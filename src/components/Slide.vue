<template>
  <transition :name="transition">
    <div v-show="visible">
      <slot></slot>
    </div>
  </transition>
</template>

<script>
export default {
  props: {
    index: { type: Number, default: 0 },
  },
  computed: {
    visible() {
      return this.index === this.$parent.index;
    },
    transition() {
      return "slide-" + this.$parent.direction;
    },
  },
};
</script>

<style>
.slide-right-enter-active {
  animation: slideIn 1s;
}

@keyframes slideIn {
  from {
    transform: translateX(100%);
  }
  to {
    transform: translateX(0);
  }
}

.slide-right-leave-active {
  animation: slideOut 1s;
  position: absolute;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
  width: 100%;
}

@keyframes slideOut {
  from {
    transform: translateX(0);
  }
  to {
    transform: translateX(-100%);
  }
}

.slide-left-enter-active {
  animation: slideLeftIn 1s;
}

@keyframes slideLeftIn {
  from {
    transform: translateX(-100%);
  }
  to {
    transform: translateX(0);
  }
}

.slide-left-leave-active {
  animation: slideLeftOut 1s;
  position: absolute;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
  width: 100%;
}

@keyframes slideLeftOut {
  from {
    transform: translateX(0);
  }
  to {
    transform: translateX(100%);
  }
}
</style>
