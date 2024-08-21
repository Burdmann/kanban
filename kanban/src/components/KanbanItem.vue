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
  },
}
</script>



<template>
    <div class="kanban-item" :id="name" draggable=true @dragstart="startDrag($event)">
        <p class="item-name">{{name}}</p>
        <p class="item-desc">{{desc}}</p>
    </div>
</template>

<style>

    .item-name {
        font-weight: bold;
        background-color: green;
        text-align: center;
        text-decoration: underline;
    }
    .item-desc {
        background-color: green;
        font-style: italic;
    }
    .kanban-item {
        margin: 10px;
        width: 200px;
    }
</style>