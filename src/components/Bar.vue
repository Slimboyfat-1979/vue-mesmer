<template>
    <div :class="barName" :style="{backgroundColor: color}"></div>
</template>

<script>
    export default {
        props: ['color', 'barName']
    }
</script>

<style scoped>
    div {
        position: absolute;
        height: 60px;
        width: 100px;
        left: 90%;
        animation: move 180s linear infinite forwards;
    }

    .one {
        top: 40%;
    }

    .two {
        top: 60%;
    }

    @keyframes move {
        0% {
            left: 90%
        }
        50% {
            left: 0
        }
        100%{
            left: 90%
        }
    }

</style>