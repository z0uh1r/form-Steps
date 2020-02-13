<template>
  <div>
    <div id="steps" class="steps">
      <div :style="{ 'width': steps }" class="steps__active"></div>
    </div>
    <div class="form">
      <form action="#">
        <transition name="slide" mode="out-in">
          <div :key="1" v-if="controls.currentStep === 1" class="form-step">
            <label>First Name:</label>
            <input type="text" v-model="person.firstName">
          </div>

          <div :key="2" v-if="controls.currentStep === 2" class="form-step">
            <label>last Name:</label>
            <input type="text" v-model="person.lastName">
          </div>

          <div :key="3" v-if="controls.currentStep === 3" class="form-step">
            <label>Age:</label>
            <input type="text" v-model="person.age">
          </div>

          <div :key="4" v-if="controls.currentStep === 4" class="form-step">
            <label>Address:</label>
            <input type="text" v-model="person.address">
          </div>

          <div :key="5" v-if="controls.currentStep === 5" class="form-step">
            <label>City:</label>
            <input type="text" v-model="person.city">
          </div>

          <div :key="6" v-if="controls.currentStep === 6" class="form-step">
            <label>State:</label>
            <input type="text" v-model="person.state">
          </div>
        </transition>
      </form>
      <div class="steps-control">
        <button @click="prevStep">Back</button>
        <button @click="nextStep">Next</button>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: "FormSteps",
    data() {
      return {
        person: {
          firstName: '',
          lastName: '',
          age: '',
          address: '',
          city: '',
          state: ''
        },
        controls: {
          currentStep: 1,
          stepsCount: 6
        }
      }
    },
    computed: {
      steps() {
        const vm = this;
        const prevStep = parseInt(vm.controls.currentStep) - 1;
        const ratio = (prevStep/vm.controls.stepsCount)*100;
        return ratio + "%";
      }
    },
    methods: {
      nextStep() {
        const vm = this;
        vm.controls.currentStep !== 6 ? vm.controls.currentStep++ : null;
      },
      prevStep() {
        const vm = this;
        vm.controls.currentStep !== 1 ? vm.controls.currentStep-- : null;
      }
    }
  }
</script>

<style lang="scss" scoped>

</style>
