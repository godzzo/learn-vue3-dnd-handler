<template>
  <div class="flex justify-center">
    <div class="w-48">
      <draggable
        class="list-group w-full flex flex-col gap-2"
        :list="state.list"
        :sort="true"
        :handle="'.handle'"
        @change="log"
        :move="checkMove"
      >
        <div
          class="p-1 rounded-md text-center flex flex-row justify-between"
          :class="'bg-' + element.color + '-100'"
          v-for="element in state.list"
          :key="element.name"
        >
          <span class="px-2">{{ element.name + ' ' + element.color }}</span>

          <div class="handle cursor-grab px-2">
            <bookmarkIcon style="width: 20px" />
          </div>
        </div>
      </draggable>
    </div>
    <rawDisplays class="w-48" :value="state.list" />
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive } from 'vue';
import { VueDraggableNext } from 'vue-draggable-next';
import bookmarkIcon from './Small.vue';
import rawDisplays from './rawDisplay.vue';
import { data } from '../data';
import { checkMove } from '../util';

export default defineComponent({
  components: {
    draggable: VueDraggableNext,
    rawDisplays,
    bookmarkIcon,
  },

  setup() {
    const state = reactive(data);

    function log(event) {
      // console.log(event)
    }

    return {
      state,
      log,
      checkMove,
    };
  },
});
</script>
