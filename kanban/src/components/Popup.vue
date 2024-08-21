<script setup lang="ts">
    defineProps<{
        show:boolean
    }>()
</script>

<script lang="ts">
    export default {
    emits: ["close"],
    methods: {
        
    }
}
</script>

<template>
    <div v-show="show" class="modal" ref="modal">
        <slot ref="content"></slot>
        <button @click="$emit('close')">close </button>
    </div>
</template>

<style>
    .modal {
        background-color: orange;
        /* position: fixed;
        z-index: 1;
        overflow: auto; */
    }
</style>