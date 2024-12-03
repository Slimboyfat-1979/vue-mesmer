<template>
    <button v-on:click="startShow">Click To Start</button>
</template>

<script>
    export default {
        methods: {
            startShow() {
                this.$emit('start')
            }
        }
    }
</script>

<style scoped>
    button {
        padding: 20px 100px;
        position: absolute;
        top: 80%;
        left: 50%;
        transform: translate(-50%, -50%);
        border: none;
        background: white;
        color: black;
        box-shadow: 5px 5px 10px black;
        border-radius: 10px;
        font-family:'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        cursor: pointer;
        font-size: 1rem;
    }
</style>