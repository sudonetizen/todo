<script lang="ts" setup>
import type { TaskFilter } from '../types';

const props = defineProps<{
    filter: TaskFilter;
    currentFilter: TaskFilter;
}>();

const emits = defineEmits<{
    setFilter: [filter: TaskFilter]
}>();

</script>

<template>
    <button
        class="secondary" 
        @click="emits('setFilter', filter)"
        :class="{ contrast: currentFilter === filter}"
    >
        {{ filter }}
    </button>
</template>


<style scoped>
    text-transform: capitalise;
</style>
