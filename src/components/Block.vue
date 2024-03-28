<template>
    <div class="block" v-if="showBlock" @click="stopTimer">
        Click Me
    </div>
  
</template>

<script>
export default {
    props: ['delay'],

    data() {
        return {
            showBlock: false,
            timer: null,
            reactionTime: 0
        }        
    },

    mounted() {
        // console.log("Block Mounted")
        setTimeout(()=> {
            this.showBlock = true
            // console.log("We are waiting for", this.delay)
            this.startTimer()
        }, this.delay)
    },

    updated() {
        // console.log("Updated block executed")
    },

    unmounted() {
        // console.log("Unmounted Block Executed")
        // console.log("Reaction time is ", this.reactionTime)
    },

    methods: {
        startTimer() {
            // console.log("Inside Start Timer")
            this.timer = setInterval(()=> {
                this.reactionTime = this.reactionTime + 10
            }, 10)
        },

        stopTimer() {
            clearInterval(this.timer)
            // console.log("Clicked on Block, Stop Timer")
            // console.log("Reaction time is ", this.reactionTime)
            this.$emit('end',this.reactionTime)
        }
    }

}
</script>

<style>
    .block {
        width: 400px;
        border-radius: 20px;
        background: rgb(77, 250, 77);
        color: white;
        text-align: center;
        padding: 100px 0;
        margin: 40px auto;
    }
</style>