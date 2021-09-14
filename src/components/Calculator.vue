<template>
  <div class="calculator">
    <h3>Tell us about you, and we’ll recommend the <br/>
    right tax solution</h3>

    <div class="calculator-area">
      <div class="steps-navigator">
        <Step 
          v-for="(step, index) in steps" 
          :key="index" 
          :title="step.title" 
          :index="index" 
          @selectStep="selectStep"
          :active="currentStep === index"/>
      </div>
      <div class="steps-list">
        <SituationSelect 
          :selected="selectedSituation"
          @selectSituation="selectSituation" 
          v-if="currentStep === 0"/>
      
      </div>
    </div>

  </div>
</template>

<script>
  import Step from './Step.vue';
  import SituationSelect from './SituationSelect.vue';

  export default{

    components: {
      Step,
      SituationSelect,
    },

    data: () => {
      return {
        currentStep: 0,
        selectedSituation: '',
        steps: [
          {
            title: 'TELL US HOW YOU\'D LIKE TO FILE',
          },
          {
            title: 'TELL US ABOUT YOUR SITUATION',
          },
          {
            title: 'YOUR RECOMMENDED PRODUCT',
          }
        ], // steps
      };
    },

    methods: {
      selectStep(step) {
        this.currentStep = parseInt(step);
      },

      selectSituation(slug) {
        this.selectedSituation = slug;
      },
    }
  }
</script>

<style scoped>
h3 {
  text-align: center;
  font-size: 44px;
  line-height: 53px;
}

.calculator {
  max-width: 1200px;
  margin: 0 auto;
}

.steps-navigator {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.steps-navigator, .steps-list {
  flex: 0 50%;
  width: 50%;
}

.calculator-area {
  padding: 25px 16px;
  display: flex;
  flex-direction: row;
  border-top: 1px solid rgba(151, 151, 151, 0.21);
  border-bottom: 1px solid rgba(151, 151, 151, 0.21);
}
</style>

