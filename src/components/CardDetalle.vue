<script setup lang="ts">
import { withDefaults } from 'vue';

type CardModel = {
    titulo: string
    descripcion: string
}

withDefaults(defineProps<CardModel>(), {
    titulo: "Hello",
    descripcion: "Vue Classmate"
})
</script>

<template>
    <div class="card w-100">
        <div class="card-body">
            <div class="card-title">
                <slot name="titulo">
                    <h3>Default Title</h3>
                </slot>
            </div>
            <p class="card-text">{{ descripcion }}</p>
            <div class="card-body">
                <slot></slot>
            </div>
        </div>
        
    </div>
</template>