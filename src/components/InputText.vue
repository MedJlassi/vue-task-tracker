<template>
    <input type="text" :value="value" @change="logging1">
</template>


<script>

export default {
    name: 'InputText',
    props: {
        value: String
    },
    methods: {
        logging1(e) {
            console.log(e.target.value, ": ", this.value)
        }
    }
}
</script>
