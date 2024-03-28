<template>
    <p>Reaction time is {{ score }} ms</p>
    <p class="rank">{{ rank }}</p>
</template>

<script>
export default {
    props: ['score'],

    data() {
        return {
            rank: null
        }
    },

    mounted() {
        // console.log("Results component mounted...")
        if (this.score < 350) {
            this.rank = "Expert Level"
        }
        else if (this.score < 500) {
            this.rank = "Good Job"            
        }
        else {
            this.rank = "Not So Well"
        }
    }
}
</script>

<style>
    .rank {
        font-size: 1.4em;
        color: rgb(84, 217, 84);
        font-weight: bold;
    }

</style>