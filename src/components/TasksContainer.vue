<template>
    <div :key="task.id" v-for="task in tasks">
        <task-element :task="task" @delete-task="(id) => $emit('delete-task', id)"
            @toggle-reminder="(id) => $emit('toggle-reminder', id)"></task-element>

    </div>
</template>



<script>
import TaskElement from './TaskElement.vue';
export default {
    name: 'TaskContainer',
    props: {
        tasks: Array,

    },
    components: {
        TaskElement
    },
    methods: {
    },
    emits: ['delete-task', 'toggle-reminder']

}

</script>


<style scoped></style>
