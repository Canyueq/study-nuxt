<template>
  <div class="min-h-screen flex flex-col">
    <NuxtRouteAnnouncer />
    <nuxt-page/>
  </div>
</template>

<style scoped>
html {
  scroll-behavior: smooth;
}

body {
  @apply bg-gray-50 text-gray-900 font-sans antialiased;
}

/* 自定义滚动条 */
::-webkit-scrollbar {
  width: 8px;
}

::-webkit-scrollbar-track {
  @apply bg-gray-100;
}

::-webkit-scrollbar-thumb {
  @apply bg-gray-300 rounded-full hover:bg-gray-400;
}

/* 文章卡片悬停效果 */
.article-card {
  @apply transition-all duration-300 hover:shadow-lg hover:-translate-y-1;
}

/* 导航栏滚动效果 */
.nav-scroll {
  @apply transition-all duration-300 bg-white/95 backdrop-blur-sm shadow-md;
}

/* 全局样式重置和基础设置 */
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

html {
  scroll-behavior: smooth;
}

body {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  @apply bg-gray-50 text-gray-900;
}
</style>
