<script setup lang="ts">
    defineProps<{
        name: string
        items: {
            name: string;
            desc: string;
            list: string;
        }[]
    }>()
</script>

<script lang="ts">
import Popup from './Popup.vue';
export default {
components: {
    Popup
},
computed: {
    getList() {
      return this.items.filter((item) => item.list === this.name)
    },
  },
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
        console.log(newItem)
        this.newItem.name = ""
        this.newItem.desc = ""
        if (this.items.find(item => item.name == newItem.name)) return // don't add items with the same name as a previous item
        this.items.push({name: newItem.name, desc: newItem.desc, list: this.name})
    }
  },
  data() {
    return {
        newItem: {name: "", desc: ""}
    }
}
}
</script>

<template>
    <v-col @drop="onDrop($event,name)" @dragover.prevent @dragenter.prevent class="d-flex flex-column">
        <h2>{{ name }}</h2>
        <KanbanItem v-for="item in getList" :name="item.name" :desc="item.desc"/>
        <v-spacer></v-spacer>
        <Popup title="Add Item" :callback="addItem">
            <v-container>
            <v-text-field
                v-model="newItem.name"
                color="primary"
                label="Item Name"
                variant="underlined"
            ></v-text-field>

            <v-text-field
                v-model="newItem.desc"
                color="primary"
                label="Item Description"
                variant="underlined"
            ></v-text-field>
            </v-container>
        </Popup>
    </v-col>
</template>