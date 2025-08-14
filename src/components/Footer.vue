
<template>
  <footer class="bg-gray-900 text-white">
    <div class="container mx-auto px-4 py-16">
      <div class="grid lg:grid-cols-4 md:grid-cols-2 gap-8">
        <!-- Logo and Description -->
        <div class="lg:col-span-1 animate-on-scroll">
          <div class="flex items-center space-x-3 mb-6">
            <div class="bg-blue-600 p-2 rounded-full">
              <component :is="BabyIcon" class="h-6 w-6 text-white" />
            </div>
            <div>
              <h3 class="text-xl font-bold">Pequenos Sonhos</h3>
              <p class="text-sm text-gray-400">Educação Infantil</p>
            </div>
          </div>
          <p class="text-gray-400 leading-relaxed mb-6">
            Há mais de 15 anos cuidando e educando crianças com amor, carinho e 
            profissionalismo. Seu filho em boas mãos.
          </p>
          
          <!-- Social Links -->
          <div class="flex space-x-4">
            <a v-for="(social, index) in socialLinks" 
               :key="index"
               :href="social.href"
               class="bg-gray-800 p-3 rounded-full hover:bg-blue-600 transition-colors"
               :aria-label="social.name">
              <component :is="social.icon" class="h-5 w-5" />
            </a>
          </div>
        </div>

        <!-- Links Sections -->
        <div class="animate-on-scroll" style="animation-delay: 0.1s">
          <h4 class="text-lg font-semibold mb-6">A Escola</h4>
          <ul class="space-y-3">
            <li v-for="(link, index) in footerLinks.escola" :key="index">
              <button @click="scrollToSection(link.href)"
                      class="text-gray-400 hover:text-white transition-colors">
                {{ link.name }}
              </button>
            </li>
          </ul>
        </div>

        <div class="animate-on-scroll" style="animation-delay: 0.2s">
          <h4 class="text-lg font-semibold mb-6">Turmas</h4>
          <ul class="space-y-3">
            <li v-for="(link, index) in footerLinks.turmas" :key="index">
              <button @click="scrollToSection(link.href)"
                      class="text-gray-400 hover:text-white transition-colors">
                {{ link.name }}
              </button>
            </li>
          </ul>
        </div>

        <!-- Contact Info -->
        <div class="animate-on-scroll" style="animation-delay: 0.3s">
          <h4 class="text-lg font-semibold mb-6">Contato</h4>
          <div class="space-y-4">
            <div class="flex items-start space-x-3">
              <component :is="PhoneIcon" class="h-5 w-5 text-blue-400 mt-1" />
              <div>
                <p class="text-white">(11) 3456-7890</p>
                <p class="text-gray-400 text-sm">WhatsApp: (11) 98765-4321</p>
              </div>
            </div>
            
            <div class="flex items-start space-x-3">
              <component :is="MailIcon" class="h-5 w-5 text-blue-400 mt-1" />
              <div>
                <p class="text-white">contato@pequenossonhos.com.br</p>
                <p class="text-gray-400 text-sm">Resposta em até 24h</p>
              </div>
            </div>
            
            <div class="flex items-start space-x-3">
              <component :is="MapPinIcon" class="h-5 w-5 text-blue-400 mt-1" />
              <div>
                <p class="text-white">Rua das Flores, 123</p>
                <p class="text-gray-400 text-sm">Vila Esperança - São Paulo/SP</p>
              </div>
            </div>
            
            <div class="flex items-start space-x-3">
              <component :is="ClockIcon" class="h-5 w-5 text-blue-400 mt-1" />
              <div>
                <p class="text-white">Seg a Sex: 7h às 18h</p>
                <p class="text-gray-400 text-sm">Sáb: 8h às 12h (visitas)</p>
              </div>
            </div>
          </div>
        </div>
      </div>

      <!-- Bottom Section -->
      <div class="border-t border-gray-800 mt-12 pt-8 animate-on-scroll" style="animation-delay: 0.4s">
        <div class="flex flex-col md:flex-row justify-between items-center space-y-4 md:space-y-0">
          <p class="text-gray-400 text-sm">
            © {{ currentYear }} Creche Pequenos Sonhos. Todos os direitos reservados.
          </p>
          <div class="flex space-x-6 text-sm">
            <a href="#" class="text-gray-400 hover:text-white transition-colors">
              Política de Privacidade
            </a>
            <a href="#" class="text-gray-400 hover:text-white transition-colors">
              Termos de Uso
            </a>
            <a href="#" class="text-gray-400 hover:text-white transition-colors">
              Cookies
            </a>
          </div>
        </div>
      </div>
    </div>
  </footer>
</template>

<script setup lang="ts">
import { computed, defineComponent, h } from 'vue'

// Icon components
const BabyIcon = defineComponent({
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

const FacebookIcon = defineComponent({
  render: () => h('svg', {
    class: 'h-5 w-5',
    fill: 'currentColor',
    viewBox: '0 0 24 24'
  }, [
    h('path', {
      d: 'M24 12.073c0-6.627-5.373-12-12-12s-12 5.373-12 12c0 5.99 4.388 10.954 10.125 11.854v-8.385H7.078v-3.47h3.047V9.43c0-3.007 1.792-4.669 4.533-4.669 1.312 0 2.686.235 2.686.235v2.953H15.83c-1.491 0-1.956.925-1.956 1.874v2.25h3.328l-.532 3.47h-2.796v8.385C19.612 23.027 24 18.062 24 12.073z'
    })
  ])
})

const InstagramIcon = defineComponent({
  render: () => h('svg', {
    class: 'h-5 w-5',
    fill: 'currentColor',
    viewBox: '0 0 24 24'
  }, [
    h('path', {
      d: 'M12.017 0C5.396 0 .029 5.367.029 11.987c0 6.62 5.367 11.987 11.988 11.987 6.62 0 11.987-5.367 11.987-11.987C24.014 5.367 18.637.001 12.017.001zM8.449 16.988c-1.297 0-2.448-.49-3.323-1.297C4.198 14.895 3.5 13.559 3.5 12.017s.698-2.878 1.626-3.674c.875-.807 2.026-1.297 3.323-1.297 1.297 0 2.448.49 3.323 1.297.928.796 1.626 2.132 1.626 3.674s-.698 2.878-1.626 3.674c-.875.807-2.026 1.297-3.323 1.297zm7.068 0c-1.297 0-2.448-.49-3.323-1.297-.928-.796-1.626-2.132-1.626-3.674s.698-2.878 1.626-3.674c.875-.807 2.026-1.297 3.323-1.297 1.297 0 2.448.49 3.323 1.297.928.796 1.626 2.132 1.626 3.674s-.698 2.878-1.626 3.674c-.875.807-2.026 1.297-3.323 1.297z'
    })
  ])
})

const YoutubeIcon = defineComponent({
  render: () => h('svg', {
    class: 'h-5 w-5',
    fill: 'currentColor',
    viewBox: '0 0 24 24'
  }, [
    h('path', {
      d: 'M23.498 6.186a3.016 3.016 0 0 0-2.122-2.136C19.505 3.545 12 3.545 12 3.545s-7.505 0-9.377.505A3.017 3.017 0 0 0 .502 6.186C0 8.07 0 12 0 12s0 3.93.502 5.814a3.016 3.016 0 0 0 2.122 2.136c1.871.505 9.376.505 9.376.505s7.505 0 9.377-.505a3.015 3.015 0 0 0 2.122-2.136C24 15.93 24 12 24 12s0-3.93-.502-5.814zM9.545 15.568V8.432L15.818 12l-6.273 3.568z'
    })
  ])
})

const PhoneIcon = defineComponent({
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
      d: 'M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z'
    })
  ])
})

const MailIcon = defineComponent({
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
      d: 'M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z'
    })
  ])
})

const MapPinIcon = defineComponent({
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

const ClockIcon = defineComponent({
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
      d: 'M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z'
    })
  ])
})

const currentYear = computed(() => new Date().getFullYear())

const footerLinks = {
  escola: [
    { name: 'Sobre Nós', href: '#sobre' },
    { name: 'Nossa Metodologia', href: '#metodologia' },
    { name: 'Galeria', href: '#galeria' },
    { name: 'Depoimentos', href: '#' }
  ],
  turmas: [
    { name: 'Maternal (0-2 anos)', href: '#turmas' },
    { name: 'Jardim (3-5 anos)', href: '#turmas' },
    { name: 'Atividades', href: '#galeria' },
    { name: 'Horários', href: '#metodologia' }
  ]
}

const socialLinks = [
  { icon: FacebookIcon, href: '#', name: 'Facebook' },
  { icon: InstagramIcon, href: '#', name: 'Instagram' },
  { icon: YoutubeIcon, href: '#', name: 'YouTube' }
]

const scrollToSection = (sectionId: string) => {
  const element = document.getElementById(sectionId.replace('#', ''))
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
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}
</style>
