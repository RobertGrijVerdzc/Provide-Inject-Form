<template>
    <div class="alert alert-primary container d-flex justify-content-between" role="alert">
        {{tarea.texto}}
        <div>
            <button @click.prevent="modificar(tarea.id)" class="btn btn-sm mx-2"><i class="fas fa-check-circle text-success"></i></button>
            <button @click.prevent="eliminar(tarea.id)" class="btn btn-sm"><i class="fas fa-minus-circle text-danger"></i></button>
        </div>
    </div>
</template>

<script>
import { inject } from '@vue/runtime-core'
export default {
    props:{
        tarea:{
            type : Object,
            required: true
        }
    },
    setup() {
        const tareas = inject('tareas')
        const eliminar = id =>{
            console.log(id)
            tareas.value = tareas.value.filter(item => item.id !== id)
        }

        const modificar = id => {
            return tareas.value = tareas.value.map(item => {
                if(item.id === id){
                    item.estado = !item.estado
                }
                return item
            })
        }

        return {eliminar, tareas,modificar }
    }
}
</script>

<style>

</style>