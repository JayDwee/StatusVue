<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <div style="display: flex">
    <StatusCard title="meowfacts" url="https://meowfacts.herokuapp.com/"/>
    <StatusCard title="wooffacts" url="https://wooffacts.herokuapp.com/"/>
  </div>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component';
import StatusCard from './components/StatusCard.vue';

@Options({
  components: {
    StatusCard,
  },
})
export default class App extends Vue {}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
