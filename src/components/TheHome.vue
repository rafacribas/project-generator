<template>
  <div class="container">
    <div style="width: 100%; display: flex; justify-content: center">
      <button @click="lockAll(true)" class="lock-all">lock all</button>
      <button @click="generate" class="generate-btn">generate</button>
      <button @click="lockAll(false)" class="lock-all">unlock all</button>
    </div>
    <div class="cards-wrapper">
      <Tech v-for="tech in techs" :key="tech.value" :name="tech.name" :isLocked="tech.isLocked"
        :clickable="tech.clickable" :value='tech.value' @click="tech.isLocked = !tech.isLocked" :link="uiLink" />
    </div>

  </div>
</template>

<script setup lang="ts">
import Tech from '@/components/TheTech.vue'

import type { Ref } from 'vue';
import { ref, onMounted, reactive } from 'vue'
const techs = reactive([
  {
    name: 'vue opt',
    isLocked: false,
    value: ''
  },
  {
    name: 'ui library',
    isLocked: false,
    clickable: true,
    value: ''
  },
  {
    name: 'render',
    isLocked: false,
    value: ''
  },
  {
    name: 'state management',
    isLocked: false,
    value: ''
  },
])
const arrUis = ref([
  {
    name: 'Nuxt UI',
    link: 'https://ui.nuxt.com/'
  },
  {
    name: 'PrimeVue',
    link: 'https://primevue.org/'
  },
  {
    name: 'Quasar',
    link: 'https://quasar.dev/'
  },
  {
    name: 'Vuetify',
    link: 'https://vuetifyjs.com/en/'
  },
  {
    name: 'Radix Vue',
    link: 'https://www.radix-vue.com/'
  },
  {
    name: 'Headless UI',
    link: 'https://headlessui.com/'
  },
  {
    name: 'Shadcn-vue',
    link: 'https://www.shadcn-vue.com/'
  },
  {
    name: 'Tailwind UI',
    link: 'https://tailwindui.com/'
  },
  {
    name: 'Naive UI',
    link: 'https://www.naiveui.com/'
  },
  {
    name: 'Daisy UI',
    link: 'https://www.naiveui.com/en-US/os-theme'
  },
  {
    name: 'Element Plus',
    link: 'https://element-plus.org'
  },
  {
    name: 'Ant Design Vue',
    link: 'https://antdv.com/'
  },
  {
    name: 'Vuestic UI',
    link: 'https://ui.vuestic.dev/'
  }
])
const arrRendering = ref(['SPA', 'SSR', 'Hybrid'])
const arrStateManagement = ref(['Pinia', 'Reactivity API'])
const uiLink = ref('')

const arrVueOpts = ref(['Vue 3 Options API', 'Vue 3 Composition API', 'Nuxt 3'])

onMounted(() => {
  generate()
})

function lockAll(lock: Boolean) {
  techs.forEach((elem) => {
    elem.isLocked = lock ? true : false;
  })
}

function generate() {
  if (!techs[0].isLocked) {
    techs[0].value = getRandom(arrVueOpts);
  }
  if (!techs[1].isLocked) {
    const arrNames = ref<string[]>([]);
    arrUis.value.forEach((elem) => arrNames.value.push(elem.name))
    const current = getRandom(arrNames)
    const link = arrUis.value.find(obj => obj.name == current)
    if (link) {
      uiLink.value = link.link
    }
    techs[1].value = current;
  }
  if (!techs[2].isLocked) {
    techs[2].value = getRandom(arrRendering);
  }
  if (!techs[3].isLocked) {
    techs[3].value = getRandom(arrStateManagement);
  }
}

function getRandom(arr: Ref<string[]>) {
  let index = Math.floor(Math.random() * arr.value.length)
  return arr.value[index]
}

</script>

<style scoped>
.container {
  padding: 0px 25%;
  margin-top: 64px;
}

.cards-wrapper {
  display: flex;
  justify-content: space-around;
  flex-wrap: wrap;
}

.lock-all {
  width: 150px;
  height: 50px;
  border-radius: 12px;
  font-size: 18px;
  padding: 8px;
  border: 0px;
  color: rgba(235, 235, 235);
  background-color: transparent;
  margin-top: 22px;

}

.lock-all:hover {
  cursor: pointer;
  text-decoration: underline;
}

.generate-btn {
  width: 200px;
  height: 70px;
  border-radius: 12px;
  font-size: 24px;
  padding: 8px;
  border: 0px;
  color: rgba(235, 235, 235);
  background-color: hsla(160, 100%, 37%, 1);
}

.generate-btn:hover {
  cursor: pointer;
  background-color: hsla(160, 100%, 37%, 0.8);
  transition: 0.4s;
}
</style>
