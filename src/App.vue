<script setup>
import draggable from 'vuedraggable'
import { ref } from 'vue'

const groups = ref([
  {
    title: 'Group 1',
    value: 'group1',
    items: [
      {
        title: 'Item 1',
        value: 'item1',
      },
      {
        title: 'Item 2',
        value: 'item2',
      },
    ],
  },
  {
    title: 'Group 2',
    value: 'group2',
    items: [
      {
        title: 'Item 3',
        value: 'item3',
      },
      {
        title: 'Item 4',
        value: 'item4',
      },
    ],
  },
])
</script>

<template>
  <v-app>
    <v-main>
      <v-card class="mx-auto mt-10" width="300" variant="outlined">
        <v-card-title>
          Drag and Drop v-list-group with VueDraggable
        </v-card-title>
        <v-divider color="black"></v-divider>

        <!-- draggable piece starts here -->
        <v-list>
          <draggable v-model="groups" group="groups" item-key="value">
            <template #item="{ element }">
              <v-list-group :key="element.value">
                <template v-slot:activator="{ props }">
                  <v-list-item
                    v-bind="props"
                    prepend-icon="mdi-account-circle"
                    :title="element.title"
                    :value="element.value"
                  ></v-list-item>
                </template>

                <v-list-item
                  v-for="item in element.items"
                  :title="item.title"
                  :value="item.value"
                ></v-list-item>
              </v-list-group>
            </template>
          </draggable>
        </v-list>

        <v-divider color="black"></v-divider>

        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn
            icon="mdi-github"
            to="https://github.com/jclong98/vuetify3-draggable-group"
          ></v-btn>
        </v-card-actions>
      </v-card>
    </v-main>
  </v-app>
</template>
