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
    <div class="kanban-item" :id="name" draggable=true @dragstart="startDrag($event)">
        <p class="item-name">{{name}}</p>
        <p class="item-desc">{{desc}}</p>
    </div>
</template>

<style scoped>

    .item-name {
        font-weight: bold;
        background-color: #fff9f3;
        text-align: center;
        text-decoration: underline;
    }
    .item-desc {
        background-color: #fff9f3;
        font-style: italic;
    }
    .kanban-item {
        outline: 1px solid #f2b8b4;
        margin: 10px;
        width: 200px;
    }
</style>