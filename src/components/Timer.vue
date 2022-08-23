<template >
    <div class="Block" v-if="showBlock" @click="StopTimer">
        Click
    </div>
</template>
<script>
export default {
    props: ['delay'],
    data() {
        return {
            showBlock: false,
            timer: null,
            reaction: 0
        }
    },
    mounted() {
        setTimeout(() => {
        this.showBlock = true;
        this.StartTimer();
        }, this.delay);
    },

    methods: {
        StartTimer() {
             this.timer = setInterval(() => {
                this.reaction +=5
             }, 5);
        },
        StopTimer(){
            clearInterval(this.timer);
            this.$emit('stop', this.reaction)
        }
    },
}
</script>
<style scoped>
 .Block {
    width: 600px;
    border-radius: 50px;
    background-color: greenyellow;
    text-transform: uppercase;
    color: red;
    text-align: center;
    padding: 100px 0;
    margin: 50px auto;
}
    
</style>