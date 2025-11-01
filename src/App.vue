<script setup>
import { ref, onMounted } from 'vue'
import LoadingSpinner from '@/components/LoadingSpinner.vue'

const isLoading = ref(true)
const hasError = ref(false)

onMounted(() => {
  // 模拟初始化过程
  setTimeout(() => {
    isLoading.value = false
  }, 1000)
})

// 错误处理
const handleError = (error) => {
  console.error('Application error:', error)
  hasError.value = true
  isLoading.value = false
}
</script>

<template>
  <div class="app-container">
    <!-- 加载状态 -->
    <LoadingSpinner 
      :is-loading="isLoading" 
      loading-text="Del0n1x Loading..." 
    />
    
    <!-- 错误状态 -->
    <div v-if="hasError" class="error-container">
      <div class="error-content">
        <h2>Oops! Something went wrong</h2>
        <p>Please refresh the page and try again.</p>
        <button @click="() => window.location.reload()" class="retry-btn">
          Retry
        </button>
      </div>
    </div>
    
    <!-- 主要内容 -->
    <div v-if="!isLoading && !hasError" class="router-view-wrapper" v-cloak>
      <router-view v-slot="{ Component }">
        <transition name="scale-slide" mode="out-in">
          <component :is="Component" @error="handleError" />
        </transition>
      </router-view>
    </div>
  </div>
</template>


<style scoped>
[v-cloak] {
  display: none;
}

.app-container {
  position: relative;
  width: 100%;
  height: 100vh;
  background-color: #0a0a0a;
}

.router-view-wrapper {
  position: relative;
  width: 100%;
  min-height: 100vh;
  /* 移除 overflow: hidden，允许页面滚动 */
}

.error-container {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #0a0a0a;
  z-index: 9998;
}

.error-content {
  text-align: center;
  color: #26eee1;
  padding: 40px;
  border-radius: 12px;
  background: rgba(38, 238, 225, 0.1);
  backdrop-filter: blur(10px);
  border: 1px solid rgba(38, 238, 225, 0.2);
}

.error-content h2 {
  margin: 0 0 16px 0;
  font-size: 24px;
  font-weight: 600;
}

.error-content p {
  margin: 0 0 24px 0;
  opacity: 0.8;
}

.retry-btn {
  padding: 12px 24px;
  background: #26eee1;
  color: #0a0a0a;
  border: none;
  border-radius: 8px;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s ease;
}

.retry-btn:hover {
  background: #1dd4c7;
  transform: translateY(-2px);
}

/* 页面过渡动画优化 */
.scale-slide-enter-active,
.scale-slide-leave-active {
  transition: all 0.4s cubic-bezier(0.25, 0.8, 0.25, 1);
}

.scale-slide-enter-from {
  opacity: 0;
  transform: translateX(30px) scale(0.95);
}

.scale-slide-enter-to {
  opacity: 1;
  transform: translateX(0) scale(1);
}

.scale-slide-leave-from {
  opacity: 1;
  transform: translateX(0) scale(1);
}

.scale-slide-leave-to {
  opacity: 0;
  transform: translateX(-30px) scale(0.95);
}

/* 移动端优化 */
@media (max-width: 768px) {
  .error-content {
    margin: 20px;
    padding: 30px 20px;
  }
  
  .error-content h2 {
    font-size: 20px;
  }
}
</style>
