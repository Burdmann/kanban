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
        <button @click="$emit('close')">Close</button>
    </div>
</template>

<style scoped>
    .modal {
        background-color: #fff9f3;

        display: flex;
        flex-direction: column;
    }
</style>