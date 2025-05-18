<script setup lang="ts">
import type { Todo } from '@/types/types';
import { onMounted, onUnmounted, ref } from 'vue';

const todo = ref<Todo | null>(null)
const cargando = ref(false)
const error = ref<any>('');
const id = ref(1)
const interval = ref(0)
let intervalRef: number | undefined;

onMounted(async () => {
    cargando.value = true
    try {
        todo.value = await fetch(`https://jsonplaceholder.typicode.com/todos/${id.value}`).then(
            (response) => response.json()
        );
        intervalRef = window.setInterval(() => {
            console.log(interval.value);
            interval.value++;
        }, 1000)
    } catch (err) {
        error.value = err
    } finally {
        cargando.value = false
    }
})

onUnmounted(() => {
    window.clearInterval(intervalRef);
})

</script>

<template>
  <div class="alert alert-primary" v-if="cargando">
    <h3>Cargando....</h3>
  </div>
  <div class="card mt-3">
    <div class="card-header">
        {{ todo?.title }}
    </div>
    <div class="card-body">
        <p class="card-text">
            {{ todo?.completed ? 'Finalizado' : 'Por Finalizar' }}
        </p>
    </div>
    <div class="card-footer">
        Contador: {{ interval }}
    </div>
  </div>
</template>

<style scoped></style>