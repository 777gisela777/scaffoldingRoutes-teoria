<template>
    <div v-if="framework">
        <h2>{{ framework.name }}</h2>
        <p>{{ framework.desc }}</p>
        <RouterLink :to="`/frameworks/${framework.id}/versions`">Veure Versions</RouterLink>
    </div>
    <p v-else>Framework no trobat.</p>
    <RouterView />
</template>
<script setup>
import { ref } from 'vue'
import { useRoute } from 'vue-router'
const route = useRoute()
const frameworkId = parseInt(route.params.id)

const frameworks = ref([
  { id: 1, name: 'Vue.js', desc: 'Progressive Framework per construir interfícies web.' },
  { id: 2, name: 'React', desc: 'Biblioteca per crear interfícies d’usuari interactives.' },
  { id: 3, name: 'Angular', desc: 'Framework complet per aplicacions empresarials.' }
])

const framework = frameworks.value.find(f => f.id === frameworkId)
</script>