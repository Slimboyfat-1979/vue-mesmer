<template>
    <div class="container">
        <Bar v-bind:class="{start: showStarted}" barName="one" color="white" :animationState="animationState"></Bar>
        <Bar v-bind:class="{start: showStarted}" barName="two" color="black" :animationState="animationState"></Bar>
        <div v-for="item in items" :key="item" class="strip">
            <div class="white"></div>
            <div class="black"></div>
        </div>
    </div>
    <Button v-on:start="startShow"></Button>
</template>

<script>
    import Bar from './Bar.vue';
    import Button from './Button.vue';
    export default {
        components: {
            Bar,
            Button
        },
        data() {
            return {
                items: [],
                barWidth: 2,
                showStarted: false,
                animationState: ''
            }
        },
        mounted() {
            this.audio = new Audio('./src/assets/music/background.mp3');
            this.calcNumberOfBars();
            window.addEventListener('resize', this.calcNumberOfBars);
        },
        methods: {
            calcNumberOfBars() {
                const viewPortWidth = window.innerWidth;
                const barWidthInPixels = (this.barWidth / 100) * viewPortWidth;
                const numberOfBars = Math.floor(viewPortWidth/barWidthInPixels);
                this.items = Array(numberOfBars).fill(0)
            },
            startShow() {
                if(!this.showStarted) {
                    this.showStarted = true;
                    this.audio.play();
                    this.animationState = 'running'
                }else{
                    this.showStarted = false;
                    this.audio.pause();
                    this.animationState = 'paused';
                }
            }
        }
        
    }
</script>

<style scoped>
    .container {
        position: relative;
        height: 100vh;
        width: 100vw;
        display: flex;
        flex-direction: row;
        overflow: hidden;
        
    }

    .strip {
        display: flex;
        flex-direction: row;
    }


    .black {
        width: 3vw;
        height: 100vh;
        background-color: black;
    }

    .white  {
        width: 3vw;
        height: 100vh;
        background-color: white;
    }
</style>