<script setup>
import AppHeader from '@/components/layout/AppHeader.vue'

import { ref, reactive, useTemplateRef, onMounted, provide } from 'vue'
import zhCn from 'element-plus/dist/locale/zh-cn.mjs'
// import en from 'element-plus/dist/locale/en.mjs'
</script>

<template>
  <el-config-provider :locale="zhCn">
    <el-container class="container">
      <el-header height="55px">
        <AppHeader />
      </el-header>
      <el-container>
        <el-aside width="250px">Aside</el-aside>
        <el-main>
          Main
          <el-table :data="[]" style="width: 100%">
            <el-table-column prop="date" label="Date" width="180" />
            <el-table-column prop="name" label="Name" width="180" />
            <el-table-column prop="address" label="Address" />
          </el-table>
        </el-main>
      </el-container>
    </el-container>
  </el-config-provider>
</template>

<style scoped>
.container {
  height: 100vh;
  width: 100vw;
}
/* header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
} */
</style>
