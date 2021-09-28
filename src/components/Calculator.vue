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
      
        <MySelect 
          :selected="selectedMySituation"
          @selectSituation="selectMySituation" 
          v-if="currentStep === 1"/>
        <button v-if="canContinue" class="step-continue">Continue</button>
      </div>
    </div>

  </div>
</template>

<script>
  import Step from './Step.vue';
  import SituationSelect from './SituationSelect.vue';
  import MySelect from './MySelect.vue';

  export default{

    components: {
      MySelect,
      Step,
      SituationSelect,
    },

    computed: {
      canContinue: function () {
        return this.currentStep < 2 ? true : false;
      },
    },

    data: () => {
      return {
        currentStep: 0,
        selectedSituation: '',
        selectedMySituation: [],
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

      selectMySituation(situation) {
        console.log({situation})
        const index = this.selectedMySituation.indexOf(situation);
        if (index === -1) {
          this.selectedMySituation.push(situation);
        } else {
          const arr = this.selectedMySituation;
          arr.splice(index, 1);
          this.selectedMySituation = arr;
        }
      }
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

.steps-list {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.calculator-area {
  padding: 25px 16px;
  display: flex;
  flex-direction: row;
  border-top: 1px solid rgba(151, 151, 151, 0.21);
  border-bottom: 1px solid rgba(151, 151, 151, 0.21);
}

.step-continue {
  border: 2px solid rgb(151, 151, 151);
  color: rgb(151, 151, 151);
  position: relative;
  bottom: 0px;
  width: 100%;
  max-width: 560px;
  height: 44px;
  border-radius: 5px;
  font-size: 16px;
  line-height: 24px;
  font-weight: 500;
  background-color: rgb(255, 255, 255);
}
</style>

