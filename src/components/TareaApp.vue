<template>
    <h1>Tareas App</h1>
    <h1>{{tareas}}</h1>
    <tarea-form/>
    <hr>
    <tarea-item v-for="tarea in tareas" :key="tarea.id" :tarea="tarea" />
</template>

<script>

import { ref } from '@vue/reactivity'
import TareaForm from './TareaForm.vue'
import { provide } from '@vue/runtime-core'
import TareaItem from './TareaItem.vue'
export default {
  components: { TareaForm, TareaItem },
    
  setup() {
    const tareas = ref([])
    provide('tareas', tareas)

    return { tareas }
  }
}
</script>