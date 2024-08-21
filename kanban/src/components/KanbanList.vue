<script setup lang="ts">
    import KanbanItem from './KanbanItem.vue'
    import Popup from './Popup.vue'
    const props = defineProps<{
        name: string
        items: {
            name: string;
            desc: string;
            list: string;
        }[]
    }>()
</script>

<script lang="ts">
export default {
    methods: {
        onDrop(evt:DragEvent, list:string) {
            if (evt.dataTransfer) {
                const itemID = evt.dataTransfer.getData('itemID')
                const item = this.items.find((item) => item.name == itemID)
                if (item)
                    item.list = list
            }
        },
        addItem() {
            const newItem = {name: this.newItem.name, desc: this.newItem.desc, list: this.name}
            this.newItem.name = ""
            this.newItem.desc = ""
            if (this.items.find(item => item.name == newItem.name)) return // don't add items with the same name as a previous item
            this.items.push({name: this.newItem.name, desc: this.newItem.desc, list: this.name})
        }
    },
    computed: {
    getList() {
      return this.items.filter((item) => item.list === this.name)
    },
  },
  data() {
    return {
        popupVisible: false,
        newItem: {name: "", desc: ""}
    }
}
}
</script>

<template>
    <div class="kanban-list" @drop="onDrop($event, name)" @dragover.prevent @dragenter.prevent>
        <h2 style="font-weight: bold; text-align: center;">{{name}}</h2>
        <KanbanItem name="" desc="" style="display: hidden;"></KanbanItem>
        <KanbanItem v-for="item in getList" :name="item.name" :desc="item.desc" :key="item.name"></KanbanItem>
        <button class="add-item" v-show="popupVisible==false" @click="popupVisible=true">+</button>
        <Popup class="add-item" :show="popupVisible" @close="popupVisible=false; newItem.name=''; newItem.desc=''" style="margin:10px;">
            <input v-model="newItem.name" placeholder="name...">
            <input v-model="newItem.desc" placeholder="description...">
            <button @click="addItem()">Add</button>
        </Popup>
    </div>
</template>

<style scoped>
    .kanban-list {
        background-color: #fff9f3;
        
        display: flex;
        width: auto;
        justify-content: start;
        flex-direction: column;
        margin: 20px;

        outline: 1px solid #381010;
    }

    .add-item {
        margin-top: auto;
        margin: 10px;
    }

</style>