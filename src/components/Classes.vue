
<template>
  <section id="turmas" class="py-20 bg-gray-50">
    <div class="container mx-auto px-4">
      <div class="text-center mb-16 animate-on-scroll">
        <h2 class="text-4xl font-bold text-gray-800 mb-4">
          Nossas <span class="text-blue-600">Turmas</span>
        </h2>
        <p class="text-xl text-gray-600 max-w-3xl mx-auto">
          Oferecemos turmas especializadas para cada faixa etária, respeitando 
          o desenvolvimento natural e as necessidades específicas de cada idade.
        </p>
      </div>

      <div class="grid lg:grid-cols-2 gap-8">
        <div v-for="(classItem, index) in classes" 
             :key="classItem.id"
             :class="[
               'rounded-2xl overflow-hidden shadow-lg hover:shadow-xl transition-all duration-300 border-2',
               classItem.bgColor,
               classItem.borderColor
             ]"
             class="animate-on-scroll"
             :style="{ animationDelay: `${index * 0.2}s` }">
          
          <!-- Header -->
          <div :class="['p-6 text-white', `bg-gradient-to-r ${classItem.color}`]">
            <div class="flex items-center space-x-4 mb-4">
              <div class="bg-white/20 p-3 rounded-full">
                <component :is="classItem.icon" class="h-8 w-8" />
              </div>
              <div>
                <h3 class="text-2xl font-bold">{{ classItem.title }}</h3>
                <p class="text-lg opacity-90">{{ classItem.age }}</p>
              </div>
            </div>
            <p class="text-white/90 leading-relaxed">
              {{ classItem.description }}
            </p>
          </div>

          <!-- Content -->
          <div class="p-6">
            <!-- Image -->
            <div class="mb-6 rounded-xl overflow-hidden">
              <img :src="classItem.image"
                   :alt="`Turma ${classItem.title}`"
                   class="w-full h-48 object-cover" />
            </div>

            <!-- Activities and Features -->
            <div class="grid md:grid-cols-2 gap-6">
              <div>
                <h4 class="text-lg font-semibold text-gray-800 mb-3 flex items-center">
                  <component :is="PaletteIcon" class="h-5 w-5 mr-2 text-blue-600" />
                  Atividades
                </h4>
                <ul class="space-y-2">
                  <li v-for="(activity, actIndex) in classItem.activities" 
                      :key="actIndex"
                      class="flex items-center text-gray-600">
                    <div class="w-2 h-2 bg-blue-400 rounded-full mr-3"></div>
                    {{ activity }}
                  </li>
                </ul>
              </div>

              <div>
                <h4 class="text-lg font-semibold text-gray-800 mb-3 flex items-center">
                  <component :is="BookOpenIcon" class="h-5 w-5 mr-2 text-blue-600" />
                  Diferenciais
                </h4>
                <ul class="space-y-2">
                  <li v-for="(feature, featIndex) in classItem.features" 
                      :key="featIndex"
                      class="flex items-center text-gray-600">
                    <div class="w-2 h-2 bg-pink-400 rounded-full mr-3"></div>
                    {{ feature }}
                  </li>
                </ul>
              </div>
            </div>

            <!-- CTA Button -->
            <div class="mt-6 pt-6 border-t border-gray-200">
              <button @click="scrollToContact"
                      :class="[
                        'w-full text-white py-3 rounded-full font-semibold hover:shadow-lg transition-all duration-300 transform hover:scale-105',
                        `bg-gradient-to-r ${classItem.color}`
                      ]">
                Saiba Mais sobre {{ classItem.title }}
              </button>
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
const BabyIcon = defineComponent({
  render: () => h('svg', {
    class: 'h-8 w-8',
    fill: 'none',
    stroke: 'currentColor',
    viewBox: '0 0 24 24'
  }, [
    h('path', {
      'stroke-linecap': 'round',
      'stroke-linejoin': 'round',
      'stroke-width': '2',
      d: 'M12 4.354a4 4 0 110 5.292M15 21H3v-1a6 6 0 0112 0v1zm0 0h6v-1a6 6 0 00-9-5.197m13.5-9a2.5 2.5 0 11-5 0 2.5 2.5 0 015 0z'
    })
  ])
})

const UsersIcon = defineComponent({
  render: () => h('svg', {
    class: 'h-8 w-8',
    fill: 'none',
    stroke: 'currentColor',
    viewBox: '0 0 24 24'
  }, [
    h('path', {
      'stroke-linecap': 'round',
      'stroke-linejoin': 'round',
      'stroke-width': '2',
      d: 'M17 20h5v-2a3 3 0 00-5.356-1.857M17 20H7m10 0v-2c0-.656-.126-1.283-.356-1.857M7 20H2v-2a3 3 0 015.356-1.857M7 20v-2c0-.656.126-1.283.356-1.857m0 0a5.002 5.002 0 019.288 0M15 7a3 3 0 11-6 0 3 3 0 016 0zm6 3a2 2 0 11-4 0 2 2 0 014 0zM7 10a2 2 0 11-4 0 2 2 0 014 0z'
    })
  ])
})

const PaletteIcon = defineComponent({
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
      d: 'M7 21a4 4 0 01-4-4V5a2 2 0 012-2h4a2 2 0 012 2v12a4 4 0 01-4 4zM7 3H5a2 2 0 00-2 2v12a4 4 0 004 4h2a2 2 0 002-2V5a2 2 0 00-2-2z'
    })
  ])
})

const BookOpenIcon = defineComponent({
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
      d: 'M12 6.253v13m0-13C10.832 5.477 9.246 5 7.5 5S4.168 5.477 3 6.253v13C4.168 18.477 5.754 18 7.5 18s3.332.477 4.5 1.253m0-13C13.168 5.477 14.754 5 16.5 5c1.747 0 3.332.477 4.5 1.253v13C19.832 18.477 18.247 18 16.5 18c-1.746 0-3.332.477-4.5 1.253'
    })
  ])
})

const classes = [
  {
    id: 'maternal',
    title: 'Maternal',
    age: '0 a 2 anos',
    icon: BabyIcon,
    color: 'from-pink-400 to-pink-600',
    bgColor: 'bg-pink-50',
    borderColor: 'border-pink-200',
    description: 'Cuidado especializado para bebês e crianças pequenas, focando no desenvolvimento motor, sensorial e emocional.',
    activities: [
      'Estimulação sensorial',
      'Desenvolvimento motor',
      'Musicalização infantil',
      'Contação de histórias',
      'Brincadeiras educativas',
      'Cuidados especializados'
    ],
    features: [
      'Berçário equipado',
      'Alimentação assistida',
      'Troca e higiene',
      'Sono monitorado',
      'Atividades sensoriais',
      'Acompanhamento individual'
    ],
    image: 'https://images.pexels.com/photos/1648377/pexels-photo-1648377.jpeg?auto=compress&cs=tinysrgb&w=800'
  },
  {
    id: 'jardim',
    title: 'Jardim',
    age: '3 a 5 anos',
    icon: UsersIcon,
    color: 'from-blue-400 to-blue-600',
    bgColor: 'bg-blue-50',
    borderColor: 'border-blue-200',
    description: 'Preparação para a vida escolar com atividades que desenvolvem autonomia, criatividade e habilidades sociais.',
    activities: [
      'Pré-alfabetização',
      'Matemática lúdica',
      'Artes e pintura',
      'Educação física',
      'Inglês básico',
      'Projetos temáticos'
    ],
    features: [
      'Salas temáticas',
      'Material didático',
      'Playground educativo',
      'Atividades em grupo',
      'Preparo escolar',
      'Desenvolvimento social'
    ],
    image: 'https://images.pexels.com/photos/8613059/pexels-photo-8613059.jpeg?auto=compress&cs=tinysrgb&w=800'
  }
]

const scrollToContact = () => {
  const element = document.getElementById('contato')
  if (element) {
    element.scrollIntoView({ behavior: 'smooth' })
  }
}
</script>

<style scoped>
.animate-on-scroll {
  animation: slideUp 0.8s ease-out;
}

@keyframes slideUp {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}
</style>
