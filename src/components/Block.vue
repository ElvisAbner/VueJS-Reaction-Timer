<template>
    <div class="block" v-show="showBlock" @click="stopTimer"> 
        Click me
    </div>
</template>

<script>
export default {
    props: ['delay'],
    data() {
        return {
            showBlock: false,
            timer: null,
            ractionTime: 0
        }
    },
    mounted() {
        console.log('component mounted')
        setTimeout(() => {
           this.showBlock = true
           console.log(this.delay) 
        }, this.delay)

    },
    
    methods: {
        startTimer() {
            this.timer = setInterval(() => {
               this.reactionTime += 10 
            }, 10);
        },
        stopTimer() {
            clearInterval(this.timer) 
            this.$emit('end', this.reactionTime)
        }
    }
}
</script>

<style>
.block {
    width: 400px;
    border-radius: 20px;
    background: #0faf87;
    color: white;
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;
}
</style>
