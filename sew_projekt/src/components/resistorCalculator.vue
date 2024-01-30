<template>
    <div class="resistor-calculator">  
      <div class="input-section mt-3">
        <label for="resistorValues" class="form-label">Widerstands Wert in Ohm Ω :</label>
        <div v-for="(value, index) in resistorValuesArray" :key="index" class="input-group mb-2">
          <input v-model="resistorValuesArray[index]" class="form-control" placeholder="Enter Resistor Value" />
          <div class="input-group-append">
            <button @click="removeInput(index)" class="btn btn-outline-danger" type="button">-</button>
          </div>
        </div>
        <button @click="addInput" class="btn btn-outline-primary" type="button">+ Add Resistor</button>
      </div>
  
      <div class="options-section mt-3">
        <label for="circuitType" class="form-label">Schaltungs Typ:</label>
        <select v-model="circuitType" id="circuitType" class="form-select">
          <option value="series">Seriel</option>
          <option value="parallel">Parallel</option>
        </select>
      </div>
  
      <div class="result-section mt-3">
        <label class="form-label">Ergebnis:</label>
        <p class="h4">{{ calculateResult() }} Ohm Ω </p>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        resistorValuesArray: [""],
        circuitType: "series",
      };
    },
    methods: {
      calculateResult() {
        const resistors = this.resistorValuesArray
          .filter((value) => value !== "")
          .map((value) => parseFloat(value.trim()));
  
        if (this.circuitType === "series") {
          return resistors.reduce((acc, val) => acc + val, 0);
        } else if (this.circuitType === "parallel") {
          return 1 / resistors.reduce((acc, val) => acc + 1 / val, 0);
        }
      },
      addInput() {
        this.resistorValuesArray.push("");
      },
      removeInput(index) {
        this.resistorValuesArray.splice(index, 1);
      },
    },
  };
  </script>
  
  <style scoped>
  .resistor-calculator {
    max-width: 400px;
    margin: auto;
    padding: 20px;
    border: 1px solid #ccc;
    border-radius: 8px;
  }
  
  .input-section, .options-section, .result-section {
    margin-bottom: 15px;
  }
  
  label {
    display: block;
    margin-bottom: 5px;
  }
  
  input, select {
    width: 100%;
    padding: 8px;
    border: 1px solid #ccc;
    border-radius: 4px;
  }
  
  p {
    font-size: 18px;
    font-weight: bold;
  }
  
  .input-group {
    width: 100%;
  }
  </style>
  