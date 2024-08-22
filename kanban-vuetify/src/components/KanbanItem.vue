<script setup lang="ts">
    defineProps<{
        name: string
        desc: string
    }>()
</script>

<script lang="ts">
export default {
methods: {
    startDrag(evt:DragEvent) {
        if (evt.dataTransfer) {
            evt.dataTransfer.dropEffect = 'move'
            evt.dataTransfer.effectAllowed = 'move'
            evt.dataTransfer.setData('itemID', this.name)
        }
    },
  }
}
</script>

<template>
    <v-card
    class="py-4"
    color="surface-variant"
    rel="noopener noreferrer"
    rounded="lg"
    :text="desc"
    target="_blank"
    :title="name"
    variant="text"
    draggable=true
    @dragstart="startDrag($event)"
    >
    <v-overlay
        opacity=".06"
        scrim="primary"
        contained
        model-value
        persistent
    />
    </v-card>
    <br>
</template>