
<template>
  <header class="fixed top-0 left-0 right-0 bg-white/95 backdrop-blur-md shadow-sm z-40">
    <div class="container mx-auto px-4">
      <div class="flex items-center justify-between h-16">
        <!-- Logo -->
        <div class="flex items-center space-x-3">
          <div class="bg-blue-600 p-2 rounded-full">
            <svg class="h-6 w-6 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 4.354a4 4 0 110 5.292M15 21H3v-1a6 6 0 0112 0v1zm0 0h6v-1a6 6 0 00-9-5.197m13.5-9a2.5 2.5 0 11-5 0 2.5 2.5 0 015 0z" />
            </svg>
          </div>
          <div>
            <h1 class="text-xl font-bold text-gray-800">Pequenos Sonhos</h1>
            <p class="text-xs text-gray-600">Educação Infantil</p>
          </div>
        </div>

        <!-- Desktop Navigation -->
        <nav class="hidden md:flex items-center space-x-8">
          <a v-for="item in navItems" 
             :key="item.href"
             @click="scrollToSection(item.href)"
             class="text-gray-700 hover:text-blue-600 font-medium transition-colors cursor-pointer">
            {{ item.name }}
          </a>
        </nav>

        <!-- Mobile Menu Button -->
        <button @click="toggleMobileMenu" 
                class="md:hidden p-2 rounded-lg hover:bg-gray-100 transition-colors">
          <svg v-if="!mobileMenuOpen" class="h-6 w-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
          </svg>
          <svg v-else class="h-6 w-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
          </svg>
        </button>
      </div>

      <!-- Mobile Menu -->
      <transition name="fade">
        <div v-if="mobileMenuOpen" class="md:hidden py-4 border-t border-gray-100">
          <nav class="flex flex-col space-y-4">
            <a v-for="item in navItems" 
               :key="item.href"
               @click="scrollToSection(item.href); toggleMobileMenu()"
               class="text-gray-700 hover:text-blue-600 font-medium transition-colors cursor-pointer">
              {{ item.name }}
            </a>
          </nav>
        </div>
      </transition>
    </div>
  </header>
</template>

<script setup lang="ts">
import { ref } from 'vue'

const mobileMenuOpen = ref(false)

const navItems = [
  { name: 'Início', href: 'inicio' },
  { name: 'Sobre', href: 'sobre' },
  { name: 'Turmas', href: 'turmas' },
  { name: 'Galeria', href: 'galeria' },
  { name: 'Saiba Mais', href: 'metodologia' },
  { name: 'Contato', href: 'contato' }
]

const toggleMobileMenu = () => {
  mobileMenuOpen.value = !mobileMenuOpen.value
}

const scrollToSection = (sectionId: string) => {
  const element = document.getElementById(sectionId)
  if (element) {
    element.scrollIntoView({ behavior: 'smooth' })
  }
}
</script>
