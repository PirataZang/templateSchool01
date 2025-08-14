
<template>
  <section id="contato" class="py-20 bg-white">
    <div class="container mx-auto px-4">
      <div class="text-center mb-16 animate-on-scroll">
        <h2 class="text-4xl font-bold text-gray-800 mb-4">
          Entre em <span class="text-blue-600">Contato</span>
        </h2>
        <p class="text-xl text-gray-600 max-w-3xl mx-auto">
          Estamos prontos para atender você e esclarecer todas as suas dúvidas. 
          Entre em contato conosco e agende uma visita!
        </p>
      </div>

      <div class="grid lg:grid-cols-2 gap-16">
        <!-- Contact Form -->
        <div class="animate-on-scroll">
          <div class="bg-blue-50 p-8 rounded-2xl">
            <h3 class="text-2xl font-bold text-gray-800 mb-6">
              Envie sua Mensagem
            </h3>
            <form @submit="handleSubmit" class="space-y-6">
              <div>
                <label for="nome" class="block text-sm font-medium text-gray-700 mb-2">
                  Nome Completo *
                </label>
                <input
                  type="text"
                  id="nome"
                  v-model="formData.nome"
                  required
                  class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent transition-colors"
                  placeholder="Seu nome completo"
                />
              </div>

              <div class="grid md:grid-cols-2 gap-4">
                <div>
                  <label for="telefone" class="block text-sm font-medium text-gray-700 mb-2">
                    Telefone *
                  </label>
                  <input
                    type="tel"
                    id="telefone"
                    v-model="formData.telefone"
                    required
                    class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent transition-colors"
                    placeholder="(11) 99999-9999"
                  />
                </div>
                <div>
                  <label for="email" class="block text-sm font-medium text-gray-700 mb-2">
                    E-mail *
                  </label>
                  <input
                    type="email"
                    id="email"
                    v-model="formData.email"
                    required
                    class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent transition-colors"
                    placeholder="seu@email.com"
                  />
                </div>
              </div>

              <div>
                <label for="mensagem" class="block text-sm font-medium text-gray-700 mb-2">
                  Mensagem *
                </label>
                <textarea
                  id="mensagem"
                  v-model="formData.mensagem"
                  required
                  rows="5"
                  class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent transition-colors resize-none"
                  placeholder="Conte-nos sobre seu interesse, idade da criança e qualquer dúvida que tenha..."
                />
              </div>

              <button
                type="submit"
                :disabled="isSubmitting"
                class="w-full bg-blue-600 text-white py-4 rounded-lg font-semibold hover:bg-blue-700 transition-colors disabled:opacity-50 disabled:cursor-not-allowed flex items-center justify-center space-x-2">
                <div v-if="isSubmitting" class="animate-spin rounded-full h-5 w-5 border-b-2 border-white"></div>
                <component v-else :is="SendIcon" class="h-5 w-5" />
                <span>{{ isSubmitting ? 'Enviando...' : 'Enviar Mensagem' }}</span>
              </button>
            </form>
          </div>
        </div>

        <!-- Contact Info -->
        <div class="space-y-8 animate-on-scroll">
          <h3 class="text-2xl font-bold text-gray-800 mb-6">
            Informações de Contato
          </h3>
          
          <div v-for="(item, index) in contactInfo" 
               :key="index"
               class="flex items-start space-x-4 p-6 bg-gray-50 rounded-xl hover:bg-gray-100 transition-colors"
               :style="{ animationDelay: `${index * 0.1}s` }">
            <div class="bg-blue-100 p-3 rounded-full">
              <component :is="item.icon" class="h-6 w-6 text-blue-600" />
            </div>
            <div>
              <h4 class="text-lg font-semibold text-gray-800 mb-1">
                {{ item.title }}
              </h4>
              <p class="text-gray-700 font-medium">{{ item.info }}</p>
              <p class="text-gray-600 text-sm">{{ item.subInfo }}</p>
            </div>
          </div>

          <!-- Map -->
          <div class="mt-8 animate-on-scroll">
            <h4 class="text-lg font-semibold text-gray-800 mb-4">
              Nossa Localização
            </h4>
            <div class="bg-gray-200 rounded-xl overflow-hidden h-64 relative">
              <iframe
                src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3657.1975!2d-46.6333824!3d-23.5505199!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x94ce5a2b2ed7f3a1%3A0x8adaaa3c2c4a4e8c!2sAv.%20Paulista%2C%20S%C3%A3o%20Paulo%20-%20SP!5e0!3m2!1spt-BR!2sbr!4v1234567890"
                width="100%"
                height="100%"
                style="border: 0"
                allowfullscreen
                loading="lazy"
                referrerpolicy="no-referrer-when-downgrade"
                title="Localização da Creche Pequenos Sonhos"
              />
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref, reactive, defineComponent, h } from 'vue'

const emit = defineEmits<{
  showToast: [message: string, type?: 'success' | 'error']
}>()

// Icon components
const SendIcon = defineComponent({
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
      d: 'M12 19l9 2-9-18-9 18 9-2zm0 0v-8'
    })
  ])
})

const PhoneIcon = defineComponent({
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
      d: 'M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z'
    })
  ])
})

const MailIcon = defineComponent({
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
      d: 'M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z'
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

const formData = reactive({
  nome: '',
  telefone: '',
  email: '',
  mensagem: ''
})

const isSubmitting = ref(false)

const contactInfo = [
  {
    icon: PhoneIcon,
    title: 'Telefone',
    info: '(11) 3456-7890',
    subInfo: 'WhatsApp: (11) 98765-4321'
  },
  {
    icon: MailIcon,
    title: 'E-mail',
    info: 'contato@pequenossonhos.com.br',
    subInfo: 'Resposta em até 24h'
  },
  {
    icon: MapPinIcon,
    title: 'Endereço',
    info: 'Rua das Flores, 123',
    subInfo: 'Vila Esperança - São Paulo/SP'
  },
  {
    icon: ClockIcon,
    title: 'Funcionamento',
    info: 'Segunda a Sexta: 7h às 18h',
    subInfo: 'Sábado: 8h às 12h (visitas)'
  }
]

const handleSubmit = async (e: Event) => {
  e.preventDefault()
  isSubmitting.value = true

  try {
    // Simulate form submission
    await new Promise(resolve => setTimeout(resolve, 1500))
    
    emit('showToast', 'Mensagem enviada com sucesso! Entraremos em contato em breve.', 'success')
    
    // Reset form
    formData.nome = ''
    formData.telefone = ''
    formData.email = ''
    formData.mensagem = ''
  } catch (error) {
    emit('showToast', 'Erro ao enviar mensagem. Tente novamente.', 'error')
  } finally {
    isSubmitting.value = false
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
