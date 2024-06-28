<template>
  <div>
    <button @click="toggleSidebar" class="toggle-btn">≡</button>
    <transition name="sidebar">
      <div :class="['sidebar', { 'sidebar-closed': !showSidebar }]">
        <!-- Sidebar content here -->
        <ul>
          <li><a href="#"></a></li>
          <li><a href="#">Option 1</a></li>
          <li><a href="#">Option 2</a></li>
          <li><a href="#">Option 3</a></li>
        </ul>
      </div>
    </transition>
    <div class="main-content" :class="{ 'main-content-closed': !showSidebar }">
      <!-- Main content here -->
      <h1>{{ msg }}</h1>
      <div class="card">
        <button type="button" @click="count++">count is {{ count }}</button>
        <p>
          Edit
          <code>components/HelloWorld.vue</code> to test HMR
        </p>
      </div>
      <p>
        Check out
        <a
          href="https://vuejs.org/guide/quick-start.html#local"
          target="_blank"
          >create-vue</a
        >, the official Vue + Vite starter
      </p>
      <p>
        Install
        <a href="https://github.com/johnsoncodehk/volar" target="_blank">Volar</a>
        in your IDE for a better DX
      </p>
      <p class="read-the-docs">Click on the Vite and Vue logos to learn more</p>
    </div>
  </div>
</template>

<style scoped>
.toggle-btn {
  position: fixed;
  top: 20px;
  left: 20px;
  z-index: 999;
}

.sidebar {
  width: 200px;
  height: 100%;
  background-color: #f2f2f2;
  position: fixed;
  top: 0;
  left: 0;
  overflow-x: hidden;
  padding-top: 20px;
  transition: width 0.5s ease, opacity 0.5s ease; /* Add transition property for smooth sidebar animation */
  opacity: 1;
}

.sidebar-closed {
  width: 0;
  opacity: 0; /* Add opacity for fade-out effect */
}

.main-content {
  margin-left: 200px;
  transition: margin-left 0.5s ease;
}

.main-content-closed {
  margin-left: 0;
}

.sidebar-enter-active,
.sidebar-leave-active {
  transition: width 0.5s ease, opacity 0.5s ease;
}

.sidebar-enter-from,
.sidebar-leave-to {
  width: 0;
  opacity: 0;
}
</style>

<script setup>
import { ref } from 'vue'

defineProps({
  msg: String,
})

const count = ref(0)
const showSidebar = ref(false) // 侧边栏默认关闭

function toggleSidebar() {
  showSidebar.value = !showSidebar.value
}
</script>
