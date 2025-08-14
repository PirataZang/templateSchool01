
<template>
  <section id="galeria" class="py-20 bg-white">
    <div class="container mx-auto px-4">
      <div class="text-center mb-16 animate-on-scroll">
        <h2 class="text-4xl font-bold text-gray-800 mb-4">
          Nossa <span class="text-blue-600">Galeria</span>
        </h2>
        <p class="text-xl text-gray-600 max-w-3xl mx-auto">
          Conheça nossas instalações e veja como as crianças se divertem e aprendem 
          em um ambiente seguro e estimulante.
        </p>
      </div>

      <!-- Gallery Grid -->
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
        <div v-for="(image, index) in images" 
             :key="index"
             @click="openLightbox(index)"
             class="group relative overflow-hidden rounded-xl shadow-lg cursor-pointer animate-on-scroll"
             :style="{ animationDelay: `${index * 0.1}s` }">
          <img :src="image.src"
               :alt="image.alt"
               class="w-full h-64 object-cover transition-transform duration-300 group-hover:scale-110" />
          <div class="absolute inset-0 bg-gradient-to-t from-black/60 via-transparent to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-300">
            <div class="absolute bottom-4 left-4 text-white">
              <span class="bg-blue-600 px-3 py-1 rounded-full text-sm font-medium">
                {{ image.category }}
              </span>
              <p class="mt-2 text-sm">{{ image.alt }}</p>
            </div>
          </div>
        </div>
      </div>

      <!-- Lightbox -->
      <transition name="lightbox">
        <div v-if="selectedImage !== null" 
             @click="closeLightbox"
             class="fixed inset-0 bg-black/90 z-50 flex items-center justify-center p-4">
          <div class="relative max-w-4xl max-h-full">
            <img :src="images[selectedImage].src"
                 :alt="images[selectedImage].alt"
                 @click.stop
                 class="max-w-full max-h-full object-contain rounded-lg" />
            
            <!-- Close Button -->
            <button @click="closeLightbox"
                    class="absolute top-4 right-4 bg-white/20 hover:bg-white/30 text-white p-2 rounded-full transition-colors">
              <component :is="XIcon" class="h-6 w-6" />
            </button>

            <!-- Navigation Buttons -->
            <button @click.stop="prevImage"
                    class="absolute left-4 top-1/2 transform -translate-y-1/2 bg-white/20 hover:bg-white/30 text-white p-2 rounded-full transition-colors">
              <component :is="ChevronLeftIcon" class="h-6 w-6" />
            </button>
            
            <button @click.stop="nextImage"
                    class="absolute right-4 top-1/2 transform -translate-y-1/2 bg-white/20 hover:bg-white/30 text-white p-2 rounded-full transition-colors">
              <component :is="ChevronRightIcon" class="h-6 w-6" />
            </button>

            <!-- Image Info -->
            <div class="absolute bottom-4 left-4 text-white">
              <span class="bg-blue-600 px-3 py-1 rounded-full text-sm font-medium">
                {{ images[selectedImage].category }}
              </span>
              <p class="mt-2">{{ images[selectedImage].alt }}</p>
              <p class="text-sm text-gray-300">
                {{ selectedImage + 1 }} de {{ images.length }}
              </p>
            </div>
          </div>
        </div>
      </transition>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref, defineComponent, h } from 'vue'

// Icon components
const XIcon = defineComponent({
  render: () => h('svg', {
    class: 'h-6 w-6',
    fill: 'none',
    stroke: 'currentColor',
    viewBox: '0 0 24 24'
  }, [
    h('path', {
      'stroke-linecap': 'round',
      'stroke-linejoin': 'round',
      'stroke-width': '2',
      d: 'M6 18L18 6M6 6l12 12'
    })
  ])
})

const ChevronLeftIcon = defineComponent({
  render: () => h('svg', {
    class: 'h-6 w-6',
    fill: 'none',
    stroke: 'currentColor',
    viewBox: '0 0 24 24'
  }, [
    h('path', {
      'stroke-linecap': 'round',
      'stroke-linejoin': 'round',
      'stroke-width': '2',
      d: 'M15 19l-7-7 7-7'
    })
  ])
})

const ChevronRightIcon = defineComponent({
  render: () => h('svg', {
    class: 'h-6 w-6',
    fill: 'none',
    stroke: 'currentColor',
    viewBox: '0 0 24 24'
  }, [
    h('path', {
      'stroke-linecap': 'round',
      'stroke-linejoin': 'round',
      'stroke-width': '2',
      d: 'M9 5l7 7-7 7'
    })
  ])
})

const selectedImage = ref<number | null>(null)

const images = [
  {
    src: 'https://images.pexels.com/photos/8613089/pexels-photo-8613089.jpeg?auto=compress&cs=tinysrgb&w=800',
    alt: 'Crianças brincando na sala de atividades',
    category: 'Atividades'
  },
  {
    src: 'https://images.pexels.com/photos/8613059/pexels-photo-8613059.jpeg?auto=compress&cs=tinysrgb&w=800',
    alt: 'Sala de aula colorida e aconchegante',
    category: 'Instalações'
  },
  {
    src: 'https://images.pexels.com/photos/8613028/pexels-photo-8613028.jpeg?auto=compress&cs=tinysrgb&w=800',
    alt: 'Crianças em atividade de pintura',
    category: 'Arte'
  },
  {
    src: 'https://images.pexels.com/photos/1648377/pexels-photo-1648377.jpeg?auto=compress&cs=tinysrgb&w=800',
    alt: 'Bebês no berçário',
    category: 'Maternal'
  },
  {
    src: 'https://images.pexels.com/photos/8613103/pexels-photo-8613103.jpeg?auto=compress&cs=tinysrgb&w=800',
    alt: 'Playground externo seguro',
    category: 'Playground'
  },
  {
    src: 'https://images.pexels.com/photos/8613067/pexels-photo-8613067.jpeg?auto=compress&cs=tinysrgb&w=800',
    alt: 'Atividade de leitura em grupo',
    category: 'Leitura'
  },
  {
    src: 'https://images.pexels.com/photos/8613074/pexels-photo-8613074.jpeg?auto=compress&cs=tinysrgb&w=800',
    alt: 'Crianças em atividade musical',
    category: 'Música'
  },
  {
    src: 'https://images.pexels.com/photos/8613039/pexels-photo-8613039.jpeg?auto=compress&cs=tinysrgb&w=800',
    alt: 'Refeitório infantil',
    category: 'Alimentação'
  },
  {
    src: 'https://images.pexels.com/photos/8613115/pexels-photo-8613115.jpeg?auto=compress&cs=tinysrgb&w=800',
    alt: 'Área de descanso',
    category: 'Descanso'
  }
]

const openLightbox = (index: number) => {
  selectedImage.value = index
  document.body.style.overflow = 'hidden'
}

const closeLightbox = () => {
  selectedImage.value = null
  document.body.style.overflow = 'auto'
}

const nextImage = () => {
  if (selectedImage.value !== null) {
    selectedImage.value = (selectedImage.value + 1) % images.length
  }
}

const prevImage = () => {
  if (selectedImage.value !== null) {
    selectedImage.value = selectedImage.value === 0 ? images.length - 1 : selectedImage.value - 1
  }
}
</script>

<style scoped>
.animate-on-scroll {
  animation: slideUp 0.5s ease-out;
}

.lightbox-enter-active,
.lightbox-leave-active {
  transition: opacity 0.3s ease;
}

.lightbox-enter-from,
.lightbox-leave-to {
  opacity: 0;
}

@keyframes slideUp {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}
</style>
