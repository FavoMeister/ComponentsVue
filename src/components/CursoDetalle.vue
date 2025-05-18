<script setup lang="ts">
//import type { PropType } from 'vue';
import type { Curso } from '@/types/types';

//const props = defineProps(['nombre', 'precio', 'categoría', 'enInventario']);
/*const props = defineProps({
    nombre: String,
    precio: Number,
    categoría: String,
    enInventario: Boolean,
});*/

/*type Curso = {
    nombre: string,
    precio: number,
    categoria: string,
    enInventario: boolean,
}*/

/*const props = defineProps({
    curso: {
        type: Object as PropType<Curso>,
        required: true,
        default: () =>({
            nombre: 'New One',
            precio: 2783,
            categoria: 'FullStack',
            enInventario: true
        }),
        validator: (curso: Curso) => curso.precio > 1400
    }
});*/

type PropType = {
    curso: Curso,
    estaActivo?: boolean
};

const props = withDefaults(defineProps<PropType>(), { estaActivo: true });

const emit = defineEmits<{
    (e: 'seleccionar-curso', curso:Curso): void
}>();

const seleccionar = (curso: Curso) => emit('seleccionar-curso', curso); //method

</script>

<template>
  <div>
    <h1>Detalle de Curso</h1>
  </div>
  <div class="card mt-3">
    <div class="card-header">
        <h2>{{ curso.nombre }}</h2>
    </div>
    <div class="card-body">
        <h5 class="cart-title">{{ curso.precio }}</h5>
        <p class="card-text">{{ curso.categoria }}</p>
        <div class="alert alert-info">
            {{ curso.enInventario? 'En Inventario' : 'Sin Existencia' }}
        </div>
    </div>
    <div class="card-footer">
        <button class="btn btn-primary" @click="seleccionar(curso)">
            Seleccionar
        </button>
    </div>
    <div class="card">
        <div class="alert alert-warning">
            {{ estaActivo ? 'Activo' : 'Inactivo' }}
        </div>
    </div>
  </div>
</template>

<style scoped></style>
