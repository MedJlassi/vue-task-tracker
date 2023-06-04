<template>
    <div :class="[task.reminder ? 'reminder' : '', 'task']" @dblclick="$emit('toggle-reminder', task.id)">
        <h3>{{ task.text }}
            <i style="color: red;" @click="onDelete(task.id)">x</i>
        </h3>
        <p>{{ task.day }}</p>
    </div>
</template>



<script>
export default {
    name: 'TaskElement',
    props: {
        task: Object,
        deleter: Function
    },
    methods: {
        onDelete(e) {
            this.$emit('delete-task', e)

        }
    }
}
</script>

<style scoped>
.task {
    background: #f4f4f4;
    margin: 5px;
    padding: 1px 20px;
    cursor: pointer;
}

.task.reminder {
    border-left: 5px solid green;

}

.task h3 {
    display: flex;
    align-items: center;
    justify-content: space-between;
}
</style>