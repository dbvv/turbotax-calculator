<template>
  <div class="step" :class="{active: active}" @click="$emit('selectStep', index)">
    <p class="step-index">Step {{ index + 1 }}</p>
    <p class="step-title">{{ title }}</p>
  </div>
</template>

<script>
  export default{
    props: [
      'index',
      'title',
      'active',
    ],
  }
</script>

<style scoped>
.step {
  transition: all 0.3s ease-in-out 0s;
  height: 109px;
  margin-bottom: 26px;
  width: 475px;
  border-radius: 4px;
  padding: 10px 40px;
  color: rgb(151, 151, 151);
  border-left: 6px;
  border: 1px solid rgb(216, 216, 216);
}

.step:hover, .step.active {
  box-shadow: rgba(0, 0, 0, 0.2) 0px 6px 24px;
  border-color: transparent;
}

.step.active {
  border: 1px solid transparent;
  border-left: 6px solid rgb(213, 43, 30);
  color: black;
}

.step:hover {
  cursor: pointer;
}

.step p {
  text-transform: uppercase;
  color: #979797;
}

.step-index {
  font-size: 12px;
}

.step-title {
  font-weight: 700;
  font-size: 18px;
}

.active .step-index {
  color: rgb(213, 43, 30);
}

.active .step-title {
  color: black;
}

</style>

