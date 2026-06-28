<script lang="ts" setup>
import type { Task } from '../types';

const props = defineProps<{
    tasks: Task[]
}>();

const emits = defineEmits<{
    toggleDone: [id: string];
    removeTask: [id: string];
}>();

</script>

<template>
    <div class="task-list">
        <article class="task" v-for="task in tasks" :key="task.id">
            <label>
                <input
                    @input="emits('toggleDone', task.id)"
                    :checked="task.done"
                    type="checkbox"
                >
                <span :class="{ done: task.done }">{{ task.title }}</span>
            </label>
        <button class="outline" @click="emits('removeTask', task.id)">remove</button>
        </article>
    </div>
</template>


<style>
.task {
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.task-list {
    margin-top: 1rem;
}

.done {
    text-decoration: line-through;
}
</style>
