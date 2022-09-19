<template>
    <div id="canvas">
        <div class="box"  @click="stopTimer"> </div>
        <div class="box"  @click="stopTimer"> </div>
        <div class="box"  @click="stopTimer"> </div>
        <div class="box"  @click="stopTimer"> </div>
    </div>
</template>

<script>
    export default {
        props: [ 'delay' ],
        data() {
            return {
                timer: null,
                reactionTime: 0,
            }
        },
        mounted() {
            const boxQuery = this.$el.querySelectorAll('#canvas .box');
            const boxLenght = boxQuery.length - 1;
            const randomNumber = Math.random() * ( boxLenght - 0 ) + 0;
            const activeBox = boxQuery[Math.round(randomNumber)];

            setTimeout(()=> {
                activeBox.innerHTML  = "Click Me";
                activeBox.classList.add("active");
                this.startTimer();
            },this.delay)
        },
        methods: {
            startTimer() {
                this.timer = setInterval(()=> {
                    this.reactionTime += 10;
                }, 10) 
            },
            stopTimer(event) {
                if (event.target.classList.contains('active')) {
                    this.$emit('end', this.reactionTime )
                    clearInterval(this.timer);
                } else {
                    this.$emit('end', false )
                }
            },
        }
    }
</script>

<style scoped>

    #canvas {
        display: grid;
        grid-template-columns: repeat(2, 1fr);
        max-width: 512px;
        margin: auto;
        margin-top: 3rem;
        gap: 0.2rem;
        padding: 0.2rem;
    }

    .box {
        width: 250px;
        height: 250px;
        background-color: #fff;
        border-radius: 10px;
        cursor: pointer;
        border: solid 2px #333;
        display: flex;
        align-items: center;
        justify-content: center;
        color: #fff;
        font-weight: 600;
    }

    .box.active {
        background-color: #29AB87;
    }

</style>