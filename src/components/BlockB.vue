<template>
    <div v-if="showModal">
        <img src="../assets/catch_me.jpg" alt="Catch me if you can" id="block" @click="stopTimer">
    </div>
</template>

<script>
export default {
    props:['delay'],
    data() {
        return {
            showModal: false,
            score: 0,
            timer: null
        }
    },
    mounted() {
        setTimeout(() => {
            this.showModal = true;
            this.startTimer()
        }, this.delay);
    },
    methods: {
        startTimer() {
            this.timer = setInterval(() => {
                this.score += 50;
            }, 50);
        },
        stopTimer() {
            clearInterval(this.timer);
            this.$emit("endGame", this.score);
        }
    }
}
</script>

<style>
    #block {
        width: 400px;
        height: 250px;
        margin: 20px auto;
        padding-top: 20px;
        border-radius: 10px;
    }
</style>