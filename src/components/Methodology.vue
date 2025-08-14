
<template>
  <section id="metodologia" class="py-20 bg-gray-50">
    <div class="container mx-auto px-4">
      <div class="text-center mb-16 animate-on-scroll">
        <h2 class="text-4xl font-bold text-gray-800 mb-4">
          Saiba <span class="text-blue-600">Mais</span>
        </h2>
        <p class="text-xl text-gray-600 max-w-3xl mx-auto">
          Conheça nossa metodologia, horários de funcionamento e valores. 
          Tudo pensado para oferecer a melhor experiência para seu filho.
        </p>
      </div>

      <!-- Methodology -->
      <div class="mb-20 animate-on-scroll">
        <h3 class="text-3xl font-bold text-gray-800 text-center mb-12">
          Nossa Metodologia
        </h3>
        <div class="grid md:grid-cols-2 lg:grid-cols-4 gap-8">
          <div v-for="(item, index) in methodologyItems" 
               :key="index"
               class="bg-white p-6 rounded-xl shadow-lg text-center hover:shadow-xl transition-shadow duration-300"
               :style="{ animationDelay: `${index * 0.1}s` }">
            <div class="bg-blue-100 p-4 rounded-full w-fit mx-auto mb-4">
              <component :is="item.icon" class="h-8 w-8 text-blue-600" />
            </div>
            <h4 class="text-lg font-semibold text-gray-800 mb-3">
              {{ item.title }}
            </h4>
            <p class="text-gray-600 text-sm leading-relaxed">
              {{ item.description }}
            </p>
          </div>
        </div>
      </div>

      <!-- Schedule and Pricing -->
      <div class="grid lg:grid-cols-2 gap-16">
        <!-- Schedule -->
        <div class="animate-on-scroll">
          <h3 class="text-3xl font-bold text-gray-800 mb-8 flex items-center">
            <component :is="ClockIcon" class="h-8 w-8 text-blue-600 mr-3" />
            Horários de Funcionamento
          </h3>
          <div class="space-y-6">
            <div v-for="(schedule, index) in scheduleInfo" 
                 :key="index"
                 class="bg-white p-6 rounded-xl shadow-lg border-l-4 border-blue-600"
                 :style="{ animationDelay: `${index * 0.1}s` }">
              <div class="flex items-center justify-between mb-2">
                <h4 class="text-lg font-semibold text-gray-800">
                  {{ schedule.period }}
                </h4>
                <span class="text-2xl font-bold text-blue-600">
                  {{ schedule.time }}
                </span>
              </div>
              <p class="text-gray-600">{{ schedule.description }}</p>
            </div>
          </div>
        </div>

        <!-- Pricing -->
        <div class="animate-on-scroll">
          <h3 class="text-3xl font-bold text-gray-800 mb-8 flex items-center">
            <component :is="DollarSignIcon" class="h-8 w-8 text-blue-600 mr-3" />
            Valores Mensais
          </h3>
          <div class="space-y-6">
            <div v-for="(plan, index) in pricing" 
                 :key="index"
                 :class="[
                   'bg-white p-6 rounded-xl shadow-lg border-2',
                   index === 2 ? 'border-blue-600 bg-blue-50' : 'border-gray-200'
                 ]"
                 :style="{ animationDelay: `${index * 0.1}s` }">
              <div class="flex items-center justify-between mb-4">
                <div>
                  <h4 class="text-lg font-semibold text-gray-800">
                    {{ plan.plan }}
                  </h4>
                  <p class="text-sm text-gray-600">{{ plan.period }}</p>
                </div>
                <div class="text-right">
                  <span class="text-3xl font-bold text-blue-600">
                    {{ plan.price }}
                  </span>
                  <p class="text-sm text-gray-600">/mês</p>
                </div>
              </div>
              <ul class="space-y-2">
                <li v-for="(feature, featIndex) in plan.features" 
                    :key="featIndex"
                    class="flex items-center text-gray-700">
                  <div class="w-2 h-2 bg-blue-600 rounded-full mr-3"></div>
                  {{ feature }}
                </li>
              </ul>
            </div>
          </div>
        </div>
      </div>

      <!-- CTA Section -->
      <div class="mt-16 bg-blue-600 rounded-2xl p-8 text-center text-white animate-on-scroll">
        <h3 class="text-3xl font-bold mb-4">
          Pronto para conhecer nossa escola?
        </h3>
        <p class="text-xl mb-8 opacity-90">
          Agende uma visita e veja pessoalmente como cuidamos e educamos seu filho.
        </p>
        <button @click="scrollToContact"
                class="bg-white text-blue-600 px-8 py-4 rounded-full text-lg font-semibold hover:bg-gray-100 transition-colors">
          Agendar Visita Agora
        </button>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { defineComponent, h } from 'vue'

// Icon components
const HeartIcon = defineComponent({
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
      d: 'M4.318 6.318a4.5 4.5 0 000 6.364L12 20.364l7.682-7.682a4.5 4.5 0 00-6.364-6.364L12 7.636l-1.318-1.318a4.5 4.5 0 00-6.364 0z'
    })
  ])
})

const BookOpenIcon = defineComponent({
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
      d: 'M12 6.253v13m0-13C10.832 5.477 9.246 5 7.5 5S4.168 5.477 3 6.253v13C4.168 18.477 5.754 18 7.5 18s3.332.477 4.5 1.253m0-13C13.168 5.477 14.754 5 16.5 5c1.747 0 3.332.477 4.5 1.253v13C19.832 18.477 18.247 18 16.5 18c-1.746 0-3.332.477-4.5 1.253'
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

const StarIcon = defineComponent({
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
      d: 'M11.049 2.927c.3-.921 1.603-.921 1.902 0l1.519 4.674a1 1 0 00.95.69h4.915c.969 0 1.371 1.24.588 1.81l-3.976 2.888a1 1 0 00-.363 1.118l1.518 4.674c.3.922-.755 1.688-1.538 1.118l-3.976-2.888a1 1 0 00-1.176 0l-3.976 2.888c-.783.57-1.838-.197-1.538-1.118l1.518-4.674a1 1 0 00-.363-1.118l-3.976-2.888c-.784-.57-.38-1.81.588-1.81h4.914a1 1 0 00.951-.69l1.519-4.674z'
    })
  ])
})

const ClockIcon = defineComponent({
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
      d: 'M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z'
    })
  ])
})

const DollarSignIcon = defineComponent({
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
      d: 'M12 8c-1.657 0-3 .895-3 2s1.343 2 3 2 3 .895 3 2-1.343 2-3 2m0-8c1.11 0 2.08.402 2.599 1M12 8V7m0 1v8m0 0v1m0-1c-1.11 0-2.08-.402-2.599-1'
    })
  ])
})

const methodologyItems = [
  {
    icon: HeartIcon,
    title: 'Educação com Afeto',
    description: 'Priorizamos o vínculo afetivo como base para o aprendizado e desenvolvimento emocional saudável.'
  },
  {
    icon: BookOpenIcon,
    title: 'Aprendizado Lúdico',
    description: 'Utilizamos brincadeiras e atividades lúdicas como ferramentas principais de ensino e descoberta.'
  },
  {
    icon: UsersIcon,
    title: 'Desenvolvimento Social',
    description: 'Promovemos a interação entre as crianças, desenvolvendo habilidades sociais e de cooperação.'
  },
  {
    icon: StarIcon,
    title: 'Individualidade Respeitada',
    description: 'Cada criança é única. Respeitamos o ritmo e as características individuais de desenvolvimento.'
  }
]

const scheduleInfo = [
  {
    period: 'Meio Período Manhã',
    time: '7h às 12h',
    description: 'Ideal para famílias que trabalham no período da tarde'
  },
  {
    period: 'Meio Período Tarde',
    time: '13h às 18h',
    description: 'Perfeito para quem trabalha pela manhã'
  },
  {
    period: 'Período Integral',
    time: '7h às 18h',
    description: 'Solução completa para pais que trabalham tempo integral'
  }
]

const pricing = [
  {
    plan: 'Maternal (0-2 anos)',
    period: 'Meio Período',
    price: 'R$ 800',
    features: [
      'Cuidados especializados',
      'Alimentação inclusa',
      'Fraldas e higiene',
      'Atividades sensoriais',
      'Relatório diário'
    ]
  },
  {
    plan: 'Jardim (3-5 anos)',
    period: 'Meio Período',
    price: 'R$ 650',
    features: [
      'Atividades pedagógicas',
      'Material didático',
      'Lanche incluso',
      'Inglês básico',
      'Educação física'
    ]
  },
  {
    plan: 'Período Integral',
    period: 'Qualquer idade',
    price: 'R$ 1.200',
    features: [
      'Todas as atividades',
      'Café, almoço e lanche',
      'Acompanhamento integral',
      'Atividades extras',
      'Flexibilidade de horários'
    ]
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
