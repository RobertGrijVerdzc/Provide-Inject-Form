<template>
  <div class="container">
          <form>
              <input v-model="textos" type="text" class="form-control">
                <button @click.prevent="Guardar" type="sumbit" class="btn my-2 btn-sm btn-blue w-100">Guardar</button>
          </form>
  </div>
</template>

<script>
import { inject, ref } from '@vue/runtime-core'
export default {
    setup() {

        const textos = ref('')
        const tareas = inject('tareas')

        const tarea = {
            texto: textos,
            estado : false,
            id: Date.now()
        }

        const Guardar = () => {
            //console.log(textos.value)
            tareas.value.push(tarea)
        }
        return {textos, tareas, tarea, Guardar}
    }
}
</script>

<style>

</style>