<template>
  <div id="app">
    <router-view></router-view>
  </div>
</template>

<script>
import FormSteps from './components/FormSteps.vue'

export default {
  name: 'App',
  components: {
    FormSteps
  },
  mounted() {
    console.log(this.$router);
  }
}
</script>
