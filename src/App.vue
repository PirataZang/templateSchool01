
<template>
  <div id="app" class="min-h-screen bg-white">
    <!-- Toast Container -->
    <div v-if="toast.show" 
         :class="[
           'fixed top-4 right-4 z-50 px-6 py-4 rounded-lg shadow-lg text-white font-medium transform transition-all duration-300',
           toast.type === 'success' ? 'bg-green-500' : 'bg-red-500',
           toast.show ? 'translate-x-0 opacity-100' : 'translate-x-full opacity-0'
         ]">
      {{ toast.message }}
    </div>

    <Header />
    <Hero />
    <About />
    <Classes />
    <Gallery />
    <Methodology />
    <Contact @show-toast="showToast" />
    <Footer />
  </div>
</template>

<script setup lang="ts">
import { reactive } from 'vue'
import Header from './components/Header.vue'
import Hero from './components/Hero.vue'
import About from './components/About.vue'
import Classes from './components/Classes.vue'
import Gallery from './components/Gallery.vue'
import Methodology from './components/Methodology.vue'
import Contact from './components/Contact.vue'
import Footer from './components/Footer.vue'

const toast = reactive({
  show: false,
  message: '',
  type: 'success' as 'success' | 'error'
})

const showToast = (message: string, type: 'success' | 'error' = 'success') => {
  toast.message = message
  toast.type = type
  toast.show = true
  
  setTimeout(() => {
    toast.show = false
  }, 4000)
}
</script>
