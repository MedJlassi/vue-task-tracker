<template>
    <header>
        <h1>{{ title }}</h1>
        <task-button class="btn" text="Add" :Handler="Handler"></task-button>
    </header>
</template>


<script>
import TaskButton from './TaskButton.vue';
export default {
    name: 'AppHeader',
    props: {
        title: String,
        Handler: {
            default: null
        }

    },
    components: {
        TaskButton
    }

}
</script>


<style scoped>
header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-top: 20px;
}
</style>