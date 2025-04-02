<script setup>
import { ElTooltip } from "element-plus";
</script>

<template>
  <el-footer class="footer">
    <h3 class="mask follow">Follow Us</h3>
    <img class="mask arrow" src="../assets/bg/arrow.png">
    <img class="mask arrow" src="../assets/bg/arrow.png">
    <img class="mask arrow" src="../assets/bg/arrow.png">
    <div class="mask social-icons">
      <el-tooltip content="Bilibili" placement="top">
        <a target="_blank" href="https://space.bilibili.com/3546725136468673" class="bilibili">
          <img src="../assets/bg/bilibili.png" width="30px" height="30px" />
        </a>
      </el-tooltip>
      <el-tooltip content="ctftime" placement="top">
        <a target="_blank" href="https://ctftime.org/team/283146" class="ctftime">
          <img src="../assets/bg/flag.png" width="30px" height="30px" />
        </a>
      </el-tooltip>
    </div>
  </el-footer>
</template>

<style scoped>
.footer {
  display: flex;
  justify-content: flex-end;
  align-items: center;
  height: 60px;
  padding-right: 40px;
  z-index: 999;
  position: fixed;
  bottom: 0;
  right:0;
}

.mask {
  font-size: 26px;
}

.follow {
  font-family: Departure;
  margin-right: 6px;
  color: rgb(17, 180, 221);
}

.social-icons a {
  margin-left: 20px;
  display: inline-block;
  color: aquamarine;
}

.bilibili:hover {
  transform: scale(1.5);
  transition: transform 0.5s ease;
}

.ctftime:hover {
  transform: scale(1.5);
  transition: transform 0.5s ease;
}

.arrow {
  animation: flow 1.2s infinite ease-in-out;
  /* 使用 flow 动画 */
  height: 24px;
  margin: 0 2px;
  /* 调整箭头之间的间距 */
}

@keyframes flow {
  0% {
    transform: translateX(0);
    /* 初始位置 */
    opacity: 1;
    /* 初始透明度 */
  }

  25% {
    transform: translateX(5px);
    /* 向右移动 */
    opacity: 0.75;
    /* 透明度降低 */
  }

  50% {
    transform: translateX(10px);
    /* 向右移动 */
    opacity: 0.5;
    /* 透明度降低 */
  }

  100% {
    transform: translateX(15px);
    /* 继续向右移动 */
    opacity: 0;
    /* 完全透明 */
  }
}

.arrow:nth-child(1) {
  animation-delay: 0s;
}

.arrow:nth-child(2) {
  animation-delay: 0.5s;
}

.arrow:nth-child(3) {
  animation-delay: 1s;
}
</style>