<script setup>
import { reactive, computed } from 'vue';
import InputFields from './components/InputFields.vue';
import SelectField from './components/SelectField.vue';
import ResultField from './components/ResultField.vue';
import ClearButton from './components/ClearButton.vue';

const estado = reactive({
  xValue: 0,
  yValue: 0,
  operation: '',
});

const updateXValue = (value) => {
  estado.xValue = value;
};

const updateYValue = (value) => {
  estado.yValue = value;
};

const updateOperation = (value) => {
  estado.operation = value;
};

const calculateResult = (x, y, op) => {
  switch (op) {
    case 'soma':
      return x + y;
    case 'subtracao':
      return x - y;
    case 'multiplicacao':
      return x * y;
    case 'divisao':
      return x === 0 ? 'Indefinido' : x / y;
    default:
      return '';
  }
};

const result = computed(() => calculateResult(estado.xValue, estado.yValue, estado.operation));

const clearValues = () => {
  estado.xValue = 0;
  estado.yValue = 0;
  estado.operation = '';
}
</script>

<template>
  <div class="container">
    <h1>Calculadora</h1>
    <InputFields :valueX="estado.xValue" :valueY="estado.yValue" :set-value-x="updateXValue"
      :set-value-y="updateYValue" />
    <SelectField :value="estado.operation" :set-Value="updateOperation" />
    <ResultField :result="result" />
    <ClearButton :clear-values="clearValues" />
  </div>
</template>

<style>
.container {
  max-width: 600px;
  width: 100%;
  margin: 48px auto;
  padding: 2rem;
  display: flex;
  flex-direction: column;
  gap: 1rem;
  background-color: rgb(241 241 241);

  box-shadow: rgba(0, 0, 0, 0.25) 0px 54px 55px, rgba(0, 0, 0, 0.12) 0px -12px 30px, rgba(0, 0, 0, 0.12) 0px 4px 6px, rgba(0, 0, 0, 0.17) 0px 12px 13px, rgba(0, 0, 0, 0.09) 0px -3px 5px;
  border-radius: 8px;
}

.row {
  width: 100%;
  margin-bottom: 1rem;
  display: flex;
  justify-content: space-between;
}

h1 {
  text-align: center;
  color: #0a0a0a;
}



h2,
label {
  color: #0a0a0a;
}

fieldset {
  border: 3px solid #5e5e5e;
  border-radius: 8px;
}

input,
select {
  border: 2px solid #5e5e5e;
}

@media (max-width: 599px) {
  h2 {
    font-size: 1rem;
  }
}
</style>
