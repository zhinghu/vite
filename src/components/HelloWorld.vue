<template>
  <div>
    <button @click="toggleSidebar" class="toggle-btn">Toggle Sidebar</button>
    <div v-if="showSidebar" class="sidebar">
      <!-- Sidebar content here -->
    </div>
    <div class="main-content">
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

<script setup>
import { ref } from 'vue'

defineProps({
  msg: String,
})

const count = ref(0)
const showSidebar = ref(true)

function toggleSidebar() {
  showSidebar.value = !showSidebar.value
}
</script>

<style scoped>
/* 添加样式控制按钮位置 */
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
  transition: 0.5s;
}

.main-content {
  margin-left: 200px;
  transition: margin-left 0.5s;
}

.sidebar-closed .sidebar {
  width: 0;
}

.sidebar-closed .main-content {
  margin-left: 0;
}
</style>