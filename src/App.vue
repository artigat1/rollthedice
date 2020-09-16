<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <app-roll-the-dice  />
</template>

<script>
import RollTheDice from './components/RollTheDice.vue'

export default {
  name: 'App',
  
    components: {
    appRollTheDice: RollTheDice,
  },
}
</script>
