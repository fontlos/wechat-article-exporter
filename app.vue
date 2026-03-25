<template>
  <div :class="isDev ? 'debug-screens' : ''" class="flex flex-col h-screen">
    <NuxtLayout>
      <NuxtPage />
    </NuxtLayout>

    <UNotifications />
    <UModals />
  </div>
</template>

<script setup lang="ts">
import { isDev } from '~/config';
import { isChromeBrowser } from '~/utils';
// 目前已知 侧边栏死掉了
// import { ModuleRegistry } from 'ag-grid-community';
// import { AllEnterpriseModule, LicenseManager } from 'ag-grid-enterprise';
// const runtimeConfig = useRuntimeConfig();
// ModuleRegistry.registerModules([AllEnterpriseModule]);
// LicenseManager.setLicenseKey(runtimeConfig.public.aggridLicense);

// 只注册包含核心功能的“社区版工具箱”
import { AllCommunityModule, ModuleRegistry } from 'ag-grid-community';
ModuleRegistry.registerModules([AllCommunityModule]);

if (!isChromeBrowser()) {
  alert('推荐使用 Chrome 浏览器。');
}
</script>

<style>
@import 'style.css';
</style>
