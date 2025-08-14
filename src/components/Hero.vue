
<template>
  <section id="inicio" class="pt-20 pb-16 bg-gradient-to-br from-blue-50 to-white">
    <div class="container mx-auto px-4">
      <div class="grid lg:grid-cols-2 gap-12 items-center">
        <!-- Content -->
        <div class="animate-fade-in">
          <h1 class="text-4xl md:text-5xl lg:text-6xl font-bold text-gray-800 leading-tight mb-6">
            Onde os <span class="text-blue-600">pequenos sonhos</span> se tornam realidade
          </h1>
          <p class="text-xl text-gray-600 mb-8 leading-relaxed">
            Educação infantil de qualidade com carinho, segurança e metodologia especializada. 
            Cuidamos do desenvolvimento integral do seu filho com amor e profissionalismo.
          </p>
          
          <!-- Features -->
          <div class="flex flex-col sm:flex-row gap-6 mb-8">
            <div v-for="feature in features" 
                 :key="feature.text"
                 class="flex items-center space-x-3">
              <div class="bg-blue-100 p-2 rounded-full">
                <component :is="feature.icon" class="h-5 w-5 text-blue-600" />
              </div>
              <span class="text-gray-700 font-medium">{{ feature.text }}</span>
            </div>
          </div>

          <!-- CTA Buttons -->
          <div class="flex flex-col sm:flex-row gap-4">
            <button @click="scrollToContact"
                    class="bg-blue-600 text-white px-8 py-4 rounded-full text-lg font-semibold hover:bg-blue-700 transition-all duration-300 transform hover:scale-105 shadow-lg hover:shadow-xl">
              Agendar Visita
            </button>
            <button @click="scrollToAbout"
                    class="border-2 border-blue-600 text-blue-600 px-8 py-4 rounded-full text-lg font-semibold hover:bg-blue-600 hover:text-white transition-all duration-300">
              Conheça Nossa Escola
            </button>
          </div>
        </div>

        <!-- Image -->
        <div class="relative animate-fade-in-delayed">
          <div class="relative rounded-2xl overflow-hidden shadow-2xl">
            <img src="https://images.pexels.com/photos/8613089/pexels-photo-8613089.jpeg?auto=compress&cs=tinysrgb&w=800"
                 alt="Crianças brincando na creche"
                 class="w-full h-[500px] object-cover" />
            <div class="absolute inset-0 bg-gradient-to-t from-blue-900/20 to-transparent"></div>
          </div>
          
          <!-- Floating Cards -->
          <div class="absolute -bottom-6 -left-6 bg-white p-4 rounded-xl shadow-lg animate-float-up">
            <div class="text-center">
              <div class="text-2xl font-bold text-blue-600">15+</div>
              <div class="text-sm text-gray-600">Anos de Experiência</div>
            </div>
          </div>
          
          <div class="absolute -top-6 -right-6 bg-white p-4 rounded-xl shadow-lg animate-float-up-delayed">
            <div class="text-center">
              <div class="text-2xl font-bold text-blue-600">200+</div>
              <div class="text-sm text-gray-600">Famílias Atendidas</div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { defineComponent, h } from 'vue'

// Icon components
const HeartIcon = defineComponent({
  render: () => h('svg', {
    class: 'h-5 w-5',
    fill: 'none',
    stroke: 'currentColor',
    viewBox: '0 0 24 24'
  }, [
    h('path', {
      'stroke-linecap': 'round',
      'stroke-linejoin': 'round',
      'stroke-width': '2',
      d: 'M4.318 6.318a4.5 4.5 0 000 6.364L12 20.364l7.682-7.682a4.5 4.5 0 00-6.364-6.364L12 7.636l-1.318-1.318a4.5 4.5 0 00-6.364 0z'
    })
  ])
})

const ShieldIcon = defineComponent({
  render: () => h('svg', {
    class: 'h-5 w-5',
    fill: 'none',
    stroke: 'currentColor',
    viewBox: '0 0 24 24'
  }, [
    h('path', {
      'stroke-linecap': 'round',
      'stroke-linejoin': 'round',
      'stroke-width': '2',
      d: 'M9 12l2 2 4-4m5.618-4.016A11.955 11.955 0 0112 2.944a11.955 11.955 0 01-8.618 3.04A12.02 12.02 0 003 9c0 5.591 3.824 10.29 9 11.622 5.176-1.332 9-6.031 9-11.622 0-1.042-.133-2.052-.382-3.016z'
    })
  ])
})

const StarIcon = defineComponent({
  render: () => h('svg', {
    class: 'h-5 w-5',
    fill: 'none',
    stroke: 'currentColor',
    viewBox: '0 0 24 24'
  }, [
    h('path', {
      'stroke-linecap': 'round',
      'stroke-linejoin': 'round',
      'stroke-width': '2',
      d: 'M11.049 2.927c.3-.921 1.603-.921 1.902 0l1.519 4.674a1 1 0 00.95.69h4.915c.969 0 1.371 1.24.588 1.81l-3.976 2.888a1 1 0 00-.363 1.118l1.518 4.674c.3.922-.755 1.688-1.538 1.118l-3.976-2.888a1 1 0 00-1.176 0l-3.976 2.888c-.783.57-1.838-.197-1.538-1.118l1.518-4.674a1 1 0 00-.363-1.118l-3.976-2.888c-.784-.57-.38-1.81.588-1.81h4.914a1 1 0 00.951-.69l1.519-4.674z'
    })
  ])
})

const features = [
  { icon: HeartIcon, text: 'Ambiente Acolhedor' },
  { icon: ShieldIcon, text: 'Segurança Total' },
  { icon: StarIcon, text: 'Ensino de Qualidade' }
]

const scrollToContact = () => {
  const element = document.getElementById('contato')
  if (element) {
    element.scrollIntoView({ behavior: 'smooth' })
  }
}

const scrollToAbout = () => {
  const element = document.getElementById('sobre')
  if (element) {
    element.scrollIntoView({ behavior: 'smooth' })
  }
}
</script>

<style scoped>
.animate-fade-in {
  animation: fadeIn 0.8s ease-out;
}

.animate-fade-in-delayed {
  animation: fadeIn 0.8s ease-out 0.2s both;
}

.animate-float-up {
  animation: floatUp 0.8s ease-out 0.5s both;
}

.animate-float-up-delayed {
  animation: floatUp 0.8s ease-out 0.7s both;
}

@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateX(-50px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

@keyframes floatUp {
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
