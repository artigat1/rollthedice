<template>
    <h1>Number is: {{ dice }}</h1>
    <div>Number of rolls: {{ rolls.length }}</div>
    <div>Total: {{ total }}</div>
    <button @click="roll()">Let's roll the dice</button>
    <button @click="restart()">Restart</button>
    <ul>
        <li v-for="(t, index) in rolls" :key="index">
            {{ t }}
        </li>
    </ul>
</template>

<script>
    import { computed, reactive, toRefs } from 'vue'

    export default {
        name: 'RollTheDice',

        setup() {
            const game = reactive({
                dice: 0,
                rolls: [],

                total: computed(() =>
                    game.rolls.reduce((accumulator, val) => {
                        return accumulator + val
                    }, 0)),
            })

            function roll() {
                game.dice = Math.floor(Math.random() * Math.floor(5)) + 1
                game.rolls.unshift(game.dice)
            }

            function restart() {
                game.dice = 0
                game.rolls = []
            }

            return {
                ...toRefs(game),
                roll,
                restart,
            }
        }
    }
</script>

