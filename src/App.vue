<script setup lang="ts">
import { ref } from 'vue';
import CursoDetalle from './components/CursoDetalle.vue';

const curso = ref({
  nombre: '',
  precio: 1487,
  categoria: 'BackEnd',
  enInventario: true
})
</script>

<template>
  <!-- <CursoDetalle :nombre="curso.nombre" :precio="curso.precio" :categoría="curso.categoria" :en-inventario="curso.enInventario"/> -->
   <CursoDetalle :curso="curso"/>
</template>

<style scoped></style>