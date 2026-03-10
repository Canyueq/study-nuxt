<template>
  <div class="min-h-screen flex flex-col">
    <NuxtRouteAnnouncer />
    
    <!-- 导航栏 -->
    <header 
      ref="navbar" 
      class="fixed top-0 left-0 right-0 z-50 transition-all duration-300 bg-transparent"
    >
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="flex items-center justify-between h-16">
          <!-- Logo -->
          <div class="flex-shrink-0">
            <a href="#" class="text-xl font-bold text-primary">MyBlog</a>
          </div>
          
          <!-- 导航链接 -->
          <nav class="hidden md:flex space-x-8">
            <a href="#" class="text-gray-900 hover:text-primary font-medium transition-colors">首页</a>
            <a href="#" class="text-gray-600 hover:text-primary font-medium transition-colors">文章</a>
            <a href="#" class="text-gray-600 hover:text-primary font-medium transition-colors">分类</a>
            <a href="#" class="text-gray-600 hover:text-primary font-medium transition-colors">关于</a>
          </nav>
          
          <!-- 行动按钮 -->
          <div class="flex items-center space-x-4">
            <button class="px-4 py-2 rounded-full bg-primary text-white hover:bg-primary/90 transition-colors">
              订阅
            </button>
          </div>
        </div>
      </div>
    </header>
    
    <!-- 主内容区 -->
    <main class="flex-grow pt-16">
      <!-- 英雄区域 -->
      <section class="relative overflow-hidden bg-gradient-to-br from-blue-50 to-indigo-50 py-20 md:py-32">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
          <div class="text-center animate-slide-up">
            <h1 class="text-4xl md:text-6xl font-bold text-gray-900 mb-6 leading-tight">
              探索技术的无限可能
            </h1>
            <p class="text-xl md:text-2xl text-gray-600 mb-10 max-w-3xl mx-auto">
              分享编程经验，记录技术成长，探索前沿科技
            </p>
            <div class="flex flex-col sm:flex-row items-center justify-center gap-4">
              <button class="px-8 py-4 rounded-full bg-primary text-white hover:bg-primary/90 text-lg font-medium transition-all duration-300 hover:shadow-lg">
                开始阅读
              </button>
              <button class="px-8 py-4 rounded-full bg-white text-primary border border-primary hover:bg-primary/5 text-lg font-medium transition-all duration-300">
                了解更多
              </button>
            </div>
          </div>
        </div>
        <!-- 装饰性元素 -->
        <div class="absolute top-0 left-0 w-full h-full overflow-hidden pointer-events-none">
          <div class="absolute -top-40 -right-40 w-80 h-80 bg-primary/10 rounded-full blur-3xl"></div>
          <div class="absolute bottom-0 left-0 w-80 h-80 bg-indigo-500/10 rounded-full blur-3xl"></div>
        </div>
      </section>
      
      <!-- 文章列表 -->
      <section class="py-16 bg-white">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
          <div class="flex items-center justify-between mb-12">
            <h2 class="text-3xl font-bold text-gray-900">最新文章</h2>
            <a href="#" class="text-primary hover:text-primary/80 font-medium flex items-center gap-2">
              查看全部 <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M14 5l7 7m0 0l-7 7m7-7H3"></path>
              </svg>
            </a>
          </div>
          
          <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
            <!-- 文章卡片 -->
            <article v-for="article in articles" :key="article.id" class="article-card bg-white rounded-xl overflow-hidden border border-gray-100">
              <div class="h-48 overflow-hidden">
                <img 
                  :src="article.image" 
                  :alt="article.title" 
                  class="w-full h-full object-cover transition-transform duration-500 hover:scale-105"
                >
              </div>
              <div class="p-6">
                <div class="flex items-center gap-2 mb-4">
                  <span class="px-3 py-1 bg-primary/10 text-primary text-sm rounded-full">{{ article.category }}</span>
                  <span class="text-gray-400 text-sm">{{ article.date }}</span>
                </div>
                <h3 class="text-xl font-bold text-gray-900 mb-3 hover:text-primary transition-colors">
                  <a href="#">{{ article.title }}</a>
                </h3>
                <p class="text-gray-600 mb-4 line-clamp-3">{{ article.excerpt }}</p>
                <div class="flex items-center justify-between">
                  <div class="flex items-center gap-3">
                    <img :src="article.author.avatar" :alt="article.author.name" class="w-8 h-8 rounded-full object-cover">
                    <span class="text-sm font-medium text-gray-700">{{ article.author.name }}</span>
                  </div>
                  <button class="text-primary hover:text-primary/80 font-medium flex items-center gap-1">
                    阅读更多 <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M14 5l7 7m0 0l-7 7m7-7H3"></path>
                    </svg>
                  </button>
                </div>
              </div>
            </article>
          </div>
        </div>
      </section>
      
      <!-- 订阅区域 -->
      <section class="py-16 bg-gradient-to-r from-primary to-indigo-600 text-white">
        <div class="max-w-4xl mx-auto px-4 sm:px-6 lg:px-8 text-center">
          <h2 class="text-3xl font-bold mb-4">订阅我的博客</h2>
          <p class="text-lg mb-8 opacity-90">获取最新文章推送，每周更新</p>
          <form class="flex flex-col sm:flex-row gap-4 max-w-xl mx-auto">
            <input 
              type="email" 
              placeholder="输入你的邮箱地址" 
              class="flex-grow px-6 py-3 rounded-full text-gray-900 focus:outline-none focus:ring-2 focus:ring-white/50"
            >
            <button class="px-8 py-3 rounded-full bg-white text-primary hover:bg-opacity-90 font-medium transition-all duration-300">
              立即订阅
            </button>
          </form>
        </div>
      </section>
    </main>
    
    <!-- 页脚 -->
    <footer class="bg-gray-900 text-white py-12">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="grid grid-cols-1 md:grid-cols-4 gap-8 mb-8">
          <div>
            <h3 class="text-xl font-bold mb-4">MyBlog</h3>
            <p class="text-gray-400 mb-4">分享编程经验，记录技术成长</p>
            <div class="flex space-x-4">
              <a href="#" class="text-gray-400 hover:text-white transition-colors">
                <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24">
                  <path d="M24 4.557c-.883.392-1.832.656-2.828.775 1.017-.609 1.798-1.574 2.165-2.724-.951.564-2.005.974-3.127 1.195-.897-.957-2.178-1.555-3.594-1.555-3.179 0-5.515 2.966-4.797 6.045-4.091-.205-7.719-2.165-10.148-5.144-1.29 2.213-.669 5.108 1.523 6.574-.806-.026-1.566-.247-2.229-.616-.054 2.281 1.581 4.415 3.949 4.89-.693.188-1.452.232-2.224.084.626 1.956 2.444 3.379 4.6 3.419-2.07 1.623-4.678 2.348-7.29 2.04 2.179 1.397 4.768 2.212 7.548 2.212 9.142 0 14.307-7.721 13.995-14.646.962-.695 1.797-1.562 2.457-2.549z"></path>
                </svg>
              </a>
              <a href="#" class="text-gray-400 hover:text-white transition-colors">
                <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24">
                  <path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zM12 0C8.741 0 8.333.014 7.053.072 2.695.272.273 2.69.073 7.052.014 8.333 0 8.741 0 12c0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98C8.333 23.986 8.741 24 12 24c3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98C15.668.014 15.259 0 12 0zm0 5.838a6.162 6.162 0 100 12.324 6.162 6.162 0 000-12.324zM12 16a4 4 0 110-8 4 4 0 010 8zm6.406-11.845a1.44 1.44 0 100 2.881 1.44 1.44 0 000-2.881z"></path>
                </svg>
              </a>
              <a href="#" class="text-gray-400 hover:text-white transition-colors">
                <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24">
                  <path d="M12 2.163c3.204 0 3.584.012 4.85.07 1.017-.609 1.798-1.574 2.165-2.724-.951.564-2.005.974-3.127 1.195-.897-.957-2.178-1.555-3.594-1.555-3.179 0-5.515 2.966-4.797 6.045-4.091-.205-7.719-2.165-10.148-5.144-1.29 2.213-.669 5.108 1.523 6.574-.806-.026-1.566-.247-2.229-.616-.054 2.281 1.581 4.415 3.949 4.89-.693.188-1.452.232-2.224.084.626 1.956 2.444 3.379 4.6 3.419-2.07 1.623-4.678 2.348-7.29 2.04 2.179 1.397 4.768 2.212 7.548 2.212 9.142 0 14.307-7.721 13.995-14.646.962-.695 1.797-1.562 2.457-2.549z"></path>
                </svg>
              </a>
            </div>
          </div>
          <div>
            <h3 class="text-lg font-semibold mb-4">快速链接</h3>
            <ul class="space-y-2">
              <li><a href="#" class="text-gray-400 hover:text-white transition-colors">首页</a></li>
              <li><a href="#" class="text-gray-400 hover:text-white transition-colors">文章</a></li>
              <li><a href="#" class="text-gray-400 hover:text-white transition-colors">分类</a></li>
              <li><a href="#" class="text-gray-400 hover:text-white transition-colors">关于</a></li>
            </ul>
          </div>
          <div>
            <h3 class="text-lg font-semibold mb-4">热门分类</h3>
            <ul class="space-y-2">
              <li><a href="#" class="text-gray-400 hover:text-white transition-colors">前端开发</a></li>
              <li><a href="#" class="text-gray-400 hover:text-white transition-colors">后端开发</a></li>
              <li><a href="#" class="text-gray-400 hover:text-white transition-colors">移动开发</a></li>
              <li><a href="#" class="text-gray-400 hover:text-white transition-colors">人工智能</a></li>
            </ul>
          </div>
          <div>
            <h3 class="text-lg font-semibold mb-4">联系我</h3>
            <ul class="space-y-2 text-gray-400">
              <li>邮箱: contact@myblog.com</li>
              <li>微信: myblog_official</li>
              <li>地址: 北京市朝阳区</li>
            </ul>
          </div>
        </div>
        <div class="border-t border-gray-800 pt-8 text-center text-gray-400">
          <p>&copy; 2026 MyBlog. 保留所有权利.</p>
        </div>
      </div>
    </footer>
  </div>
</template>



<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

// 导航栏滚动效果
const navbar = ref(null)

const handleScroll = () => {
  if (window.scrollY > 50) {
    navbar.value.classList.add('nav-scroll')
  } else {
    navbar.value.classList.remove('nav-scroll')
  }
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})

// 模拟文章数据
const articles = [
  {
    id: 1,
    title: 'Vue 3 Composition API 深入探究',
    excerpt: '本文深入探讨 Vue 3 Composition API 的核心概念、使用方法和最佳实践，帮助你更好地理解和应用这一强大的 API。',
    category: '前端开发',
    date: '2026-03-01',
    image: 'https://picsum.photos/seed/vue1/600/400',
    author: {
      name: '张三',
      avatar: 'https://picsum.photos/seed/author1/100/100'
    }
  },
  {
    id: 2,
    title: 'Node.js 性能优化实战',
    excerpt: '分享一些实用的 Node.js 性能优化技巧和工具，帮助你构建更高效、更稳定的后端服务。',
    category: '后端开发',
    date: '2026-02-28',
    image: 'https://picsum.photos/seed/node1/600/400',
    author: {
      name: '李四',
      avatar: 'https://picsum.photos/seed/author2/100/100'
    }
  },
  {
    id: 3,
    title: 'React Native 跨平台开发指南',
    excerpt: '从零开始学习 React Native，掌握跨平台移动应用开发的核心技术和最佳实践。',
    category: '移动开发',
    date: '2026-02-25',
    image: 'https://picsum.photos/seed/react1/600/400',
    author: {
      name: '王五',
      avatar: 'https://picsum.photos/seed/author3/100/100'
    }
  },
  {
    id: 4,
    title: 'Python 数据分析入门',
    excerpt: '介绍 Python 数据分析的基本概念和常用库，帮助你快速上手数据分析工作。',
    category: '数据分析',
    date: '2026-02-22',
    image: 'https://picsum.photos/seed/python1/600/400',
    author: {
      name: '赵六',
      avatar: 'https://picsum.photos/seed/author4/100/100'
    }
  },
  {
    id: 5,
    title: 'Docker 容器化部署实践',
    excerpt: '详细介绍 Docker 容器化部署的流程和最佳实践，帮助你构建更可靠的部署系统。',
    category: 'DevOps',
    date: '2026-02-20',
    image: 'https://picsum.photos/seed/docker1/600/400',
    author: {
      name: '孙七',
      avatar: 'https://picsum.photos/seed/author5/100/100'
    }
  },
  {
    id: 6,
    title: 'JavaScript 设计模式详解',
    excerpt: '深入讲解 JavaScript 中常用的设计模式，帮助你写出更优雅、更可维护的代码。',
    category: '前端开发',
    date: '2026-02-18',
    image: 'https://picsum.photos/seed/js1/600/400',
    author: {
      name: '周八',
      avatar: 'https://picsum.photos/seed/author6/100/100'
    }
  }
]
</script>
