
<template>
  <section id="sobre" class="py-20 bg-white">
    <div class="container mx-auto px-4">
      <div class="grid lg:grid-cols-2 gap-16 items-center">
        <!-- Content -->
        <div class="animate-on-scroll">
          <h2 class="text-4xl font-bold text-gray-800 mb-6">
            Sobre a <span class="text-blue-600">Creche Pequenos Sonhos</span>
          </h2>
          <p class="text-lg text-gray-600 mb-8 leading-relaxed">
            Há mais de 15 anos cuidando e educando crianças com amor e dedicação. 
            Nossa missão é proporcionar um ambiente seguro, estimulante e acolhedor 
            onde cada criança pode desenvolver seu potencial único.
          </p>
          <p class="text-lg text-gray-600 mb-8 leading-relaxed">
            Acreditamos que a educação infantil é a base para o futuro. Por isso, 
            oferecemos uma metodologia pedagógica inovadora que respeita o ritmo 
            de cada criança, promovendo o desenvolvimento cognitivo, emocional, 
            social e motor.
          </p>
          
          <div class="bg-blue-50 p-6 rounded-xl">
            <h3 class="text-xl font-semibold text-gray-800 mb-3">Nossa Missão</h3>
            <p class="text-gray-700">
              Educar e cuidar de crianças de 0 a 5 anos, promovendo seu desenvolvimento 
              integral através de atividades lúdicas, educativas e seguras, em parceria 
              com as famílias.
            </p>
          </div>
        </div>

        <!-- Features Grid -->
        <div class="grid sm:grid-cols-2 gap-6 animate-on-scroll">
          <div v-for="(feature, index) in features" 
               :key="index"
               class="bg-white p-6 rounded-xl shadow-lg hover:shadow-xl transition-shadow duration-300 border border-gray-100"
               :style="{ animationDelay: `${index * 0.1}s` }">
            <div class="bg-blue-100 p-3 rounded-full w-fit mb-4">
              <component :is="feature.icon" class="h-6 w-6 text-blue-600" />
            </div>
            <h3 class="text-lg font-semibold text-gray-800 mb-2">
              {{ feature.title }}
            </h3>
            <p class="text-gray-600 text-sm leading-relaxed">
              {{ feature.description }}
            </p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { defineComponent, h } from 'vue'

// Icon components
const UsersIcon = defineComponent({
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
      d: 'M12 4.354a4 4 0 110 5.292M15 21H3v-1a6 6 0 0112 0v1zm0 0h6v-1a6 6 0 00-9-5.197m13.5-9a2.5 2.5 0 11-5 0 2.5 2.5 0 015 0z'
    })
  ])
})

const AwardIcon = defineComponent({
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
      d: 'M9 12l2 2 4-4M7.835 4.697a3.42 3.42 0 001.946-.806 3.42 3.42 0 014.438 0 3.42 3.42 0 001.946.806 3.42 3.42 0 013.138 3.138 3.42 3.42 0 00.806 1.946 3.42 3.42 0 010 4.438 3.42 3.42 0 00-.806 1.946 3.42 3.42 0 01-3.138 3.138 3.42 3.42 0 00-1.946.806 3.42 3.42 0 01-4.438 0 3.42 3.42 0 00-1.946-.806 3.42 3.42 0 01-3.138-3.138 3.42 3.42 0 00-.806-1.946 3.42 3.42 0 010-4.438 3.42 3.42 0 00.806-1.946 3.42 3.42 0 013.138-3.138z'
    })
  ])
})

const ClockIcon = defineComponent({
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
      d: 'M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z'
    })
  ])
})

const MapPinIcon = defineComponent({
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
      d: 'M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z'
    }),
    h('path', {
      'stroke-linecap': 'round',
      'stroke-linejoin': 'round',
      'stroke-width': '2',
      d: 'M15 11a3 3 0 11-6 0 3 3 0 016 0z'
    })
  ])
})

const features = [
  {
    icon: UsersIcon,
    title: "Equipe Especializada",
    description: "Professores qualificados em pedagogia e educação infantil, com formação continuada."
  },
  {
    icon: AwardIcon,
    title: "Metodologia Reconhecida",
    description: "Abordagem pedagógica baseada no desenvolvimento integral da criança."
  },
  {
    icon: ClockIcon,
    title: "Horário Flexível",
    description: "Funcionamento de segunda a sexta, das 7h às 18h, adaptando-se à rotina das famílias."
  },
  {
    icon: MapPinIcon,
    title: "Localização Privilegiada",
    description: "Ambiente seguro e acessível, com fácil acesso para os pais."
  }
]
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
