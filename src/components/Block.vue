<template>
    <div @click="endTime" v-if="showBlock" class="block d-none d-md-block">
        <span>Click Here</span>
    </div>

    <div @click="endTime" v-if="showBlock" class="block-phone d-block d-md-none">
        <span>Click Here</span>
    </div>
</template>

<script>
    export default {
        props : ['waitingTime'],
        data() {
            return {
                showBlock: false,
                score : 0,
                timer : null,
            }
        },
        methods: {
            startTime() {
                this.timer = setInterval(() => {
                    this.score +=50;
                }, 50);
            },
            endTime(){
                clearInterval(this.timer);
                this.$emit('ended',this.score);
            }
        },
        mounted () {
            setTimeout(() => {
                this.showBlock = true;
                this.startTime();
            }, this.waitingTime);
        },
    }
</script>

<style scoped>
.block{
    width: 470px;
    height: 400px;
    background-color: #c5e3f6;
    border-radius: 10px;
    margin: 30px auto;
    cursor: pointer;
    position: relative;
}

.block-phone{
    width: 300px;
    height: 300px;
    background-color: #c5e3f6;
    border-radius: 10px;
    margin: 30px auto;
    cursor: pointer;
    position: relative;
}

span{
    position: absolute;
    top: 40%;
    right: 40%;
    color: #000000;
    letter-spacing: 1px;
    font-size: 18px;
}

</style>