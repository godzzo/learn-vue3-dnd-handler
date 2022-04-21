<template>
  <div class="flex justify-center">
    <div class="w-48">
      <draggable
        class="list-group w-full flex flex-col gap-2"
        :list="state.list"
        :sort="true"
        @change="log"
        :move="checkMove"
      >
        <div
          class="p-1 rounded-md text-center cursor-grab"
          :class="'bg-' + element.color + '-100'"
          v-for="element in state.list"
          :key="element.name"
        >
          {{ element.name + ' ' + element.color }}
        </div>
      </draggable>
    </div>
    <rawDisplays class="w-48" :value="state.list" />
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive } from 'vue';
import { VueDraggableNext } from 'vue-draggable-next';
import rawDisplays from './rawDisplay.vue';
export default defineComponent({
  components: {
    draggable: VueDraggableNext,
    rawDisplays,
  },
  setup() {
    const state = reactive({
      list: [
        { name: 'John', id: 1, color: 'red' },
        { name: 'Joao', id: 2, color: 'green' },
        { name: 'Jean', id: 3, color: 'blue' },
        { name: 'Gerard', id: 4, color: 'yellow' },
      ],
    });
    function log(event) {
      // console.log(event)
    }
    function checkMove(evt) {
      console.log('Future index: ' + evt.draggedContext.futureIndex);
      console.log('element: ' + evt.draggedContext.element.name);
    }
    return {
      state,
      log,
      checkMove,
    };
  },
});
</script>

<style scoped></style>
