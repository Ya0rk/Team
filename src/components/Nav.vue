<template>
    <div class="top-nav">
        <div class="container">
            <!-- Logo 区域 -->
            <div class="nav-brand">
                <img class="logo-img" src="/Del0n1x.svg" alt="Del0n1x Logo" />
                <div class="logo-text"> Del0n1x </div>
            </div>
            
            <!-- 桌面端菜单 -->
            <nav class="desktop-menu">
                <router-link to="/home" class="nav-link" active-class="active">Home</router-link>
                <router-link to="/mem" class="nav-link" active-class="active">Members</router-link>
                <router-link to="/awards" class="nav-link" active-class="active">Awards</router-link>
                <a href="https://drive.del0n1x.com/" target="_blank" class="nav-link" rel="noopener noreferrer">Tools</a>
                <a href="https://www.yuque.com/keyboard-ovrmx/scxvuu" target="_blank" class="nav-link" rel="noopener noreferrer">WriteUp</a>
            </nav>
            
            <!-- 移动端菜单按钮 -->
            <button class="mobile-menu-btn" @click="toggleMobileMenu" :class="{ active: isMobileMenuOpen }">
                <span></span>
                <span></span>
                <span></span>
            </button>
        </div>
        
        <!-- 移动端菜单 -->
        <div class="mobile-menu" :class="{ 'mobile-open': isMobileMenuOpen }">
            <router-link to="/home" class="mobile-nav-link" active-class="active" @click="closeMobileMenu">Home</router-link>
            <router-link to="/mem" class="mobile-nav-link" active-class="active" @click="closeMobileMenu">Members</router-link>
            <router-link to="/awards" class="mobile-nav-link" active-class="active" @click="closeMobileMenu">Awards</router-link>
            <a href="https://drive.del0n1x.com/" target="_blank" class="mobile-nav-link" rel="noopener noreferrer">Tools</a>
            <a href="https://www.yuque.com/keyboard-ovrmx/scxvuu" target="_blank" class="mobile-nav-link" rel="noopener noreferrer">WriteUp</a>
        </div>
    </div>
</template>

<script setup>
import { ref } from 'vue'

const isMobileMenuOpen = ref(false)

const toggleMobileMenu = () => {
    isMobileMenuOpen.value = !isMobileMenuOpen.value
}

const closeMobileMenu = () => {
    isMobileMenuOpen.value = false
}
</script>

<style scoped>
/* 基础样式 */
.top-nav {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    z-index: 1000;
    background-color: rgba(0, 0, 0, 0.95);
    backdrop-filter: blur(10px);
    height: 70px;
    border-bottom: 1px solid rgba(38, 238, 225, 0.1);
}

.container {
    display: flex;
    align-items: center;
    justify-content: space-between;
    height: 100%;
    max-width: 1400px;
    margin: 0 auto;
    padding: 0 30px;
}

/* Logo 区域 */
.nav-brand {
    display: flex;
    align-items: center;
    gap: 15px;
    flex-shrink: 0;
}

.logo-img {
    width: 40px;
    height: 40px;
    object-fit: contain;
}

.logo-text {
    font-family: 'JetBrains Mono', monospace;
    font-size: 24px;
    color: rgb(38, 238, 225);
    font-weight: bold;
}

/* 桌面端菜单 */
.desktop-menu {
    display: flex;
    align-items: center;
    gap: 40px;
    margin-left: 60px;
}

.nav-link {
    text-decoration: none;
    color: rgba(255, 255, 255, 0.8);
    font-family: 'JetBrains Mono', monospace;
    font-size: 16px;
    font-weight: 500;
    padding: 8px 16px;
    border-radius: 6px;
    transition: all 0.3s ease;
    position: relative;
    white-space: nowrap;
}

.nav-link:hover {
    color: rgb(38, 238, 225);
    background-color: rgba(38, 238, 225, 0.1);
    transform: translateY(-2px);
}

.nav-link.active {
    color: rgb(38, 238, 225);
    background-color: rgba(38, 238, 225, 0.15);
    border-bottom: 2px solid rgb(38, 238, 225);
}

/* 移动端菜单按钮 */
.mobile-menu-btn {
    display: none;
    flex-direction: column;
    justify-content: space-around;
    width: 30px;
    height: 30px;
    background: transparent;
    border: none;
    cursor: pointer;
    padding: 0;
    z-index: 1001;
}

.mobile-menu-btn span {
    width: 100%;
    height: 3px;
    background-color: rgb(38, 238, 225);
    border-radius: 2px;
    transition: all 0.3s ease;
}

.mobile-menu-btn.active span:nth-child(1) {
    transform: rotate(45deg) translate(8px, 8px);
}

.mobile-menu-btn.active span:nth-child(2) {
    opacity: 0;
}

.mobile-menu-btn.active span:nth-child(3) {
    transform: rotate(-45deg) translate(8px, -8px);
}

/* 移动端菜单 */
.mobile-menu {
    position: fixed;
    top: 70px;
    left: 0;
    right: 0;
    background-color: rgba(0, 0, 0, 0.98);
    backdrop-filter: blur(15px);
    padding: 20px 0;
    transform: translateY(-100%);
    opacity: 0;
    visibility: hidden;
    transition: all 0.3s ease;
    box-shadow: 0 4px 20px rgba(0, 0, 0, 0.3);
    display: none;
}

.mobile-menu.mobile-open {
    transform: translateY(0);
    opacity: 1;
    visibility: visible;
}

.mobile-nav-link {
    display: block;
    text-decoration: none;
    color: rgba(255, 255, 255, 0.8);
    font-family: 'JetBrains Mono', monospace;
    font-size: 18px;
    font-weight: 500;
    padding: 15px 30px;
    border-bottom: 1px solid rgba(38, 238, 225, 0.1);
    transition: all 0.3s ease;
}

.mobile-nav-link:hover,
.mobile-nav-link.active {
    color: rgb(38, 238, 225);
    background-color: rgba(38, 238, 225, 0.1);
}

.mobile-nav-link:last-child {
    border-bottom: none;
}

/* 响应式设计 */
@media (max-width: 1200px) {
    .desktop-menu {
        gap: 30px;
        margin-left: 40px;
    }
    
    .nav-link {
        font-size: 15px;
        padding: 6px 12px;
    }
}

@media (max-width: 900px) {
    .desktop-menu {
        gap: 20px;
        margin-left: 30px;
    }
    
    .nav-link {
        font-size: 14px;
        padding: 6px 10px;
    }
}

@media (max-width: 768px) {
    .desktop-menu {
        display: none;
    }
    
    .mobile-menu-btn {
        display: flex;
    }
    
    .mobile-menu {
        display: block;
    }
    
    .container {
        padding: 0 20px;
    }
    
    .logo-text {
        font-size: 20px;
    }
    
    .logo-img {
        width: 35px;
        height: 35px;
    }
}

@media (max-width: 480px) {
    .top-nav {
        height: 60px;
    }
    
    .mobile-menu {
        top: 60px;
    }
    
    .container {
        padding: 0 15px;
    }
    
    .logo-text {
        font-size: 18px;
    }
    
    .logo-img {
        width: 30px;
        height: 30px;
    }
    
    .mobile-nav-link {
        font-size: 16px;
        padding: 12px 20px;
    }
}
</style>