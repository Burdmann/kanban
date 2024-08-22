<script lang="ts">
export default {
    data() {
        return {
            lists: ["To do","Doing","Done"],
            items: [
                {name: "name", desc: "...", list:"To do"},
                {name: "other name", desc: "This one has a really long description. This means I can see what happens when it has to use multiple lines :).", list:"To do"}
            ],
            popupVisible: false,
            newList: ""
        };
    },
    methods: {
        addList() {
            const newList = this.newList
            this.newList = ""
            if (this.lists.includes(newList)) return // don't add lists with the same name as a previous list
            this.lists.push(newList)
        }
    }
    };
</script>

<template>
    <v-container class="fill-height">
      <v-responsive
        class="align-center fill-height mx-auto"
        max-width="1800"
        min-height="1000"
      >
  
        <v-row>
            <KanbanList v-for="name in lists" :name="name" :items="items"/>
            <v-col>
                <Popup title="Add List" :callback="addList">
                    <v-container>
                <v-text-field
                    v-model="newList"
                    color="primary"
                    label="List Name"
                    variant="underlined"
                ></v-text-field>
                </v-container>
                </Popup>
            </v-col>
        </v-row>
      </v-responsive>
    </v-container>
  </template>
