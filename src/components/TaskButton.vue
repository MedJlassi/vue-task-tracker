<template>
    <button @click="Handler" :style="{ background: color }"> {{ text }}</button>
</template>


<script>

export default {
    name: 'TaskButton',
    props: {
        text: String,
        color: String,
        Handler: {
            default: null
        }

    },
    methods: {
        onclick() {
            alert('clicked')
        }
    }
}
</script>