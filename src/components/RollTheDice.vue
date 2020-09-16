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
    import { computed, ref } from 'vue'

    export default {
        name: 'RollTheDice',

        setup() {
            const dice = ref(0)
            const rolls = ref([])

            function roll() {
                dice.value = Math.floor(Math.random() * Math.floor(5)) + 1
                rolls.value.unshift(dice.value)
            }

            function restart() {
                dice.value = 0
                rolls.value = []
            }

            const total = computed(() =>
                rolls.value.reduce((accumulator, val) => {
                    return accumulator + val
                }, 0))

            return {
                dice,
                rolls,
                total,
                roll,
                restart,
            }
        }
    }
</script>

