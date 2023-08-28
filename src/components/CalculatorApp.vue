<template>
  <div class="calculator-container">
    <div class="calculator bg-success p-4 text-white rounded">
      <div class="d-flex justify-content-between">
        <div class="mb-3 flex-grow-1 me-2">
          <label for="num1" class="form-label">Número 1</label>
          <input type="number" class="form-control" id="num1" v-model="number1" />
        </div>
        <div class="mb-3 flex-grow-1 me-2">
          <label for="operation" class="form-label">Operação</label>
          <select class="form-select" id="operation" v-model="selectedOperation">
            <option value="add">Adição (+)</option>
            <option value="subtract">Subtração (-)</option>
            <option value="multiply">Multiplicação (*)</option>
            <option value="divide">Divisão (/)</option>
          </select>
        </div>
        <div class="mb-3 flex-grow-1">
          <label for="num2" class="form-label">Número 2</label>
          <input type="number" class="form-control" id="num2" v-model="number2" />
        </div>
      </div>
      <button class="btn btn-primary mx-auto d-block mb-2" @click="calculate">Calcular</button>
      <div class="result text-center">
        Resultado: {{ result }}
      </div>
    </div>
  </div>
</template>



<script>
export default {
  data() {
    return {
      number1: 0,
      number2: 0,
      selectedOperation: 'add',
      result: 0 // Adicionei a propriedade result aqui
    };
  },
  methods: {
    calculate(e) {
      e.preventDefault(); // Correção aqui
      
      let result = 0;

      switch (this.selectedOperation) {
        case 'add':
          result = parseFloat(this.number1) + parseFloat(this.number2);
          break;
        case 'subtract':
          result = parseFloat(this.number1) - parseFloat(this.number2);
          break;
        case 'multiply':
          result = parseFloat(this.number1) * parseFloat(this.number2);
          break;
        case 'divide':
          result = parseFloat(this.number1) / parseFloat(this.number2);
          break;
        default:
          break;
      }

      // Atualize o valor do resultado
      this.result = result;
    }
  }
};
</script>


<style scoped>
.calculator-container {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
}
</style>
