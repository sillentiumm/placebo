<template>
  <button
    class="btn"
    @mouseenter="handleMouseEnter"
    @mouseleave="handleMouseLeave"
    ref="buttonRef"
  >
    {{ title }}
    <div class="btn__ripple" ref="rippleRef"></div>
  </button>
</template>

<script setup>
import { ref, onMounted } from 'vue';

const props = defineProps({
  title: {
    type: String,
    required: true
  }
});

const buttonRef = ref(null);
const rippleRef = ref(null);

const handleMouseEnter = (e) => {
  const ripple = rippleRef.value;
  ripple.classList.remove('is-active');
  const rect = buttonRef.value.getBoundingClientRect();
  const x = e.clientX - rect.left - ripple.offsetWidth / 2;
  const y = e.clientY - rect.top - ripple.offsetHeight / 2;
  ripple.style.top = `${y}px`;
  ripple.style.left = `${x}px`;
  ripple.classList.add('is-active');
};

const handleMouseLeave = (e) => {
  const ripple = rippleRef.value;
  const rect = buttonRef.value.getBoundingClientRect();
  const x = e.clientX - rect.left - ripple.offsetWidth / 2;
  const y = e.clientY - rect.top - ripple.offsetHeight / 2;
  ripple.style.top = `${y}px`;
  ripple.style.left = `${x}px`;
  ripple.classList.remove('is-active');
};

onMounted(() => {
  const button = buttonRef.value;
  const ripple = rippleRef.value;
  const d = Math.max(button.offsetWidth, button.offsetHeight);
  ripple.style.height = `${d}px`;
  ripple.style.width = `${d}px`;
  ripple.style.position = 'absolute';
});
</script>

<style>
.btn {
  position: relative;
  width: 138px;
  height: 36px;
  color: #565656;
  background-color: transparent;
  border-radius: 8px;
  border: 1px  solid #505050;
  overflow: hidden;
  cursor: pointer;
}

.btn__ripple {
  background: rgba(0, 0, 0, 0.3);
  background: rgba(255, 255, 255, 0.3);
  border-radius: 50%;
  transform: scale(0);
  pointer-events: none;
  position: absolute;
  transition: transform 0.5s, opacity 0.75s;
}

.btn__ripple.is-active {
  transform: scale(2);
  opacity: 0;
}

</style>