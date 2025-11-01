<template>
  <div class="loading-container" v-if="isLoading">
    <div class="loading-spinner">
      <div class="spinner-ring"></div>
      <div class="loading-text">{{ loadingText }}</div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const props = defineProps({
  isLoading: {
    type: Boolean,
    default: true
  },
  loadingText: {
    type: String,
    default: 'Loading...'
  }
})
</script>

<style scoped>
.loading-container {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: #0a0a0a;
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 9999;
  backdrop-filter: blur(10px);
}

.loading-spinner {
  text-align: center;
  color: #26eee1;
}

.spinner-ring {
  width: 60px;
  height: 60px;
  border: 3px solid rgba(38, 238, 225, 0.2);
  border-top: 3px solid #26eee1;
  border-radius: 50%;
  margin: 0 auto 20px;
  animation: spin 1s linear infinite;
}

@keyframes spin {
  0% { transform: rotate(0deg); }
  100% { transform: rotate(360deg); }
}

.loading-text {
  font-family: 'JetBrains Mono', monospace;
  font-size: 16px;
  font-weight: 500;
  letter-spacing: 1px;
  animation: pulse 2s ease-in-out infinite;
}

@keyframes pulse {
  0%, 100% { opacity: 0.6; }
  50% { opacity: 1; }
}

/* 移动端优化 */
@media (max-width: 768px) {
  .spinner-ring {
    width: 50px;
    height: 50px;
  }
  
  .loading-text {
    font-size: 14px;
  }
}
</style>