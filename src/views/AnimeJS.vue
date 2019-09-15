<template>
    <div class="container">
        <div class="group">
            <button @click="group1">Start</button>
            <div class="box" ref="group1"></div>
        </div>
        <div class="group">
            <button @click="group2">Start</button>
            <div class="box" ref="group2_1"></div>
            <div class="box" ref="group2_2"></div>
            <div class="box" ref="group2_3"></div>
        </div>
        <div class="group">
            <button @click="group3">Start</button>
            <div class="box" ref="group3"></div>
        </div>
        <div class="group">
            <button @click="group4">Start</button>
            <div class="box" ref="group4"></div>
        </div>
        <div class="group">
            <button @click="group5">Start</button>
            <div class="circle" ref="group5"></div>
        </div>
    </div>
</template>

<script>
    import anime from "animejs";

    export default {
        methods: {
            group1() {
                anime({
                    targets: this.$refs.group1,
                    borderRadius: ["0%", "50%"],
                    easing: "easeInOutQuad",
                    translateX: 270
                });
            },
            group2() {
                const { group2_1, group2_2, group2_3 } = this.$refs;
                anime({
                    targets: [group2_1, group2_2, group2_3],
                    translateX: 250
                });
            },
            group3() {
                anime({
                    targets: this.$refs.group3,
                    translateX: {
                        value: 250,
                        duration: 800
                    },
                    rotate: {
                        value: 360,
                        duration: 1800,
                        easing: "easeInOutSine"
                    },
                    scale: {
                        value: 2,
                        duration: 1600,
                        delay: 800,
                        easing: "easeInOutQuart"
                    },
                    delay: 250
                });
            },
            group4() {
                anime({
                    targets: this.$refs.group4,
                    width: "100%", // -> from '28px' to '100%',
                    easing: "easeInOutQuad",
                    direction: "alternate",
                    loop: true
                });
            },
            group5() {
                this.$refs.group5.style.transform ="translateX(80px)"
                anime({
                    targets: this.$refs.group5,
                    translateX: {
                        value: "*=2.5", // 100px * 2.5 = '250px'
                        duration: 1000
                    },
                    width: {
                        value: "-=20px", // 28 - 20 = '8px'
                        duration: 1800,
                        easing: "easeInOutSine"
                    },
                    rotate: {
                        value: "+=2turn", // 0 + 2 = '2turn'
                        duration: 1800,
                        easing: "easeInOutSine"
                    },
                    direction: "alternate"
                });
            }
        }
    };
</script>

<style lang="scss" scoped>
    .container {
        display: grid;
        grid-gap: 10px;
        grid-template-columns: auto auto auto auto;
        padding: 24px;
        height: calc(100% - 78px);
    }

    .group {
        height: 150px;
        border: 2px solid #2c3e50;
        border-radius: 24px;
        display: flex;
        justify-content: space-around;
        align-content: center;
        flex-direction: column;
        padding: 8px;

        button {
            padding: 8px;
            width: 25%;
            background: transparent;
            border: 2px solid #42b983;
            color: #42b983;
            border-radius: 16px;
            align-self: center;
            outline: none;
        }
    }

    .box {
        width: 50px;
        height: 50px;
        background: red;
        margin: 4px;
    }
    .circle {
        width: 50px;
        height: 50px;
        border-radius: 25px;
        background: red;
        margin: 4px;
    }
</style>
