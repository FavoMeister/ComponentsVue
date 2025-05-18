<script setup lang="ts">
import { ref } from 'vue';

const estaOculto = ref(false);
const cerrar = () => (estaOculto.value = true);
</script>

<template>
    <div class="alert alert-primary" v-if="!estaOculto">
        <h4 class="alert-heading">
            <slot name="titulo" :cerrarAlerta="cerrar"></slot>
        </h4>
        <div class="alert-body">
            <slot></slot>
        </div>
        <hr>
        <div class="alert-footer">
            <button type="button" class="btn btn-close" data-bs-dismiss="alert" aria-label="Close" @click="cerrar"></button>
        </div>
    </div>
</template>