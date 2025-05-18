<script setup lang="ts">
import { ref } from 'vue';
import CursoDetalle from './components/CursoDetalle.vue';
import type { Curso } from '@/types/types';

const curso = ref<Curso>({
  nombre: '',
  precio: 1487,
  categoria: 'BackEnd',
  enInventario: true
});

const cursoSeleccionado = ref<Curso | null>(null);

const seleccionarCurso = (curso: Curso) => cursoSeleccionado.value = curso;
</script>

<template>
  <!-- <CursoDetalle :nombre="curso.nombre" :precio="curso.precio" :categoría="curso.categoria" :en-inventario="curso.enInventario"/> -->
   <CursoDetalle :curso="curso" @seleccionar-curso="seleccionarCurso($event)"/>
   <hr>
   <div class="alert alert-secondary">
    <pre>
      {{ cursoSeleccionado }}
    </pre>
   </div>
</template>

<style scoped></style>