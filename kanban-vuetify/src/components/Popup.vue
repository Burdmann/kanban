      
<script setup lang="ts">
    defineProps<{
        title: string
        callback: ()=>void
    }>()
</script>

<script lang="ts">
    export default {

    }
</script>


<template>
    <v-dialog max-width="500">
  <template v-slot:activator="{ props: activatorProps }">
    <v-btn
      v-bind="activatorProps"
      color="surface-variant"
      :text="title"
      variant="flat"
    ></v-btn>
  </template>

  <template v-slot:default="{ isActive }">
    <v-card
                class="mx-auto"
                max-width="344"
                :title="title"
            >
                <slot ref="content"></slot>

                <v-divider></v-divider>

                <v-card-actions>
                <v-spacer></v-spacer>

                <v-btn color="red" @click="isActive.value = false">
                    <v-icon icon="mdi-chevron-left" start></v-icon>
                    Cancel
                </v-btn>

                <v-btn color="success" @click="callback(); isActive.value = false">
                    {{ title }}
                    <v-icon icon="mdi-chevron-right" end></v-icon>
                </v-btn>
                </v-card-actions>
            </v-card>
  </template>
</v-dialog>
</template>