<script setup lang="ts">
import { ref } from 'vue';
import CursoDetalle from './components/CursoDetalle.vue';
import type { Curso } from '@/types/types';
import TodoDetalle from './components/TodoDetalle.vue';

const curso = ref<Curso>({
  nombre: '',
  precio: 1487,
  categoria: 'BackEnd',
  enInventario: true
});

const cursoSeleccionado = ref<Curso | null>(null);
const mostrarTodo = ref<boolean>(true);

const seleccionarCurso = (curso: Curso) => cursoSeleccionado.value = curso;
const toggleTodo = () => mostrarTodo.value = !mostrarTodo.value

</script>

<template>
  <!-- <CursoDetalle :nombre="curso.nombre" :precio="curso.precio" :categoría="curso.categoria" :en-inventario="curso.enInventario"/> -->
  <!-- <CursoDetalle :curso="curso" @seleccionar-curso="seleccionarCurso($event)"/>
  <hr>
  <div class="alert alert-secondary">
  <pre>
    {{ cursoSeleccionado }}
  </pre>
  </div> -->
  <button class="btn btn-primary" @click="toggleTodo">Alternan visualización de "Tarea por Hacer"</button>
  <TodoDetalle v-if="mostrarTodo"/>
</template>

<style scoped></style>