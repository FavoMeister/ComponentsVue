<script setup lang="ts">
import { ref } from 'vue';
import CursoDetalle from './components/CursoDetalle.vue';
import type { Curso } from '@/types/types';
import TodoDetalle from './components/TodoDetalle.vue';
import CardDetalle from './components/CardDetalle.vue';
import AlertaComponent from './components/AlertaComponent.vue';

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

const contador = ref(0)

setInterval(() => {
  contador.value++;
}, 1000);
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
  <!-- <button class="btn btn-primary" @click="toggleTodo">Alternan visualización de "Tarea por Hacer"</button>
  <TodoDetalle v-if="mostrarTodo"/> -->
  <!-- <CardDetalle titulo="Vue Slots" descripcion="Wonderful Vue Course with TypeScript">
    <template v-slot:titulo>
      <h2>Hello from Title <span class="text-end text-muted">Other Subtitle</span></h2>
    </template>
    <template #default>
      <h1>Hello from a default Slot</h1>
      <div class="alert alert-danger">Error</div>
      <h3>{{ contador }}</h3>
    </template>
  </CardDetalle> -->
  <AlertaComponent>
    <template #titulo="tituloProps">
      <h3 @click="tituloProps.cerrarAlerta">Importa Information</h3>
    </template>
    Lorem ipsum dolor sit amet consectetur adipisicing elit. Perspiciatis pariatur repellat sunt officiis quod omnis, mollitia delectus quia temporibus quis maxime. Nobis rem, quisquam dolorum quas minus ut vero eaque!
  </AlertaComponent>
</template>

<style scoped></style>