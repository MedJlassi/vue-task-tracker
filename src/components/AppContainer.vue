<template>
    <div class="container">
        <AppHeader title="Task Tracker" :Handler="showTaskData"></AppHeader>
        <AddForm></AddForm>
        <TasksContainer :tasks="tasksData" @delete-task="(id) => onDelete(id)"
            @toggle-reminder="(id) => onToggleReminder(id)"></TasksContainer>

    </div>
</template>

<script>
import AppHeader from './AppHeader.vue'
import TasksContainer from './TasksContainer.vue'
import AddForm from './AddForm.vue'


export default {
    name: 'AppContainer',
    components: {
        AppHeader,
        TasksContainer,
        AddForm
    },
    data() {
        return {

            tasksData: [
                { id: 1, text: 'watch the tuto for vue', day: 'jun 4 2023', reminder: true },
                { id: 2, text: 'go to the faculty', day: 'jun 8 2023', reminder: true },
                { id: 3, text: 'go home from faculty', day: 'jun 16 2023', reminder: false }
            ]
        }
    },
    methods: {
        /**factory to create objects with Crud Methods*/
        onDelete(id) {
            if (this.tasksData.length > 0) {
                if (confirm('Delete Task ?')) {
                    this.tasksData = this.tasksData.filter(ele => ele.id !== id)

                }
            }
        },
        onAdd(text, day, reminder) {
            const task = {
                id: this.tasksData.length,
                text: text,
                day: day,
                reminder: reminder
            }
            this.tasksData = [...this.tasksData, task]
        },
        onToggleReminder(id) {
            console.log(id)
            this.tasksData = this.tasksData.map(
                (task) => task.id === id ? { ...task, reminder: !task.reminder } : task
            )
        },
        showTaskData() {
            this.tasksData.forEach(ele => console.log({ ele }))
        },
        logg(e) {
            console.log(e)
        }

    },
    created() {

    }

}
</script>

<style>
* {
    box-sizing: border-box;
    margin: 0;
    padding: 0;

}

body {
    
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}

.container {
    max-width: 500px;
    margin: 30px auto;
    overflow: auto;
    min-height: 300px;
    border: 1px solid steelblue;
    padding: 30px;
    border-radius: 5px;
}

.btn {
    display: inline-block;
    background: #000;
    color: #fff;
    border: none;
    padding: 10px 20px;
    margin: 5px;
    border-radius: 5px;
    cursor: pointer;
    text-decoration: none;
    font-size: 15px;
    font-family: inherit;
}
</style>
