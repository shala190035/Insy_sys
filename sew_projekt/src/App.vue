<template>
  <div id="app" class="container">
    <div class="container">
      <div class="accordion" id="accordionExample">
        <div class="accordion-item">
          <h2 class="accordion-header">
            <button class="accordion-button" type="button" data-bs-toggle="collapse" data-bs-target="#collapseOne" aria-expanded="true" aria-controls="collapseOne">
              R-Calc
            </button>
          </h2>
          <div id="collapseOne" class="accordion-collapse collapse show" data-bs-parent="#accordionExample">
            <div class="accordion-body">
              <strong><resistor-calculator /></strong> 
            </div>
          </div>
        </div>
      </div>
    </div>
    </div>
  
</template>

<script>
import ResistorCalculator from "@/components/resistorCalculator.vue";

export default {
  name: "App",
  components: {
    ResistorCalculator,
  },
};
</script>

<style>
body {
  font-family: 'Arial', sans-serif;
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

#app {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
  background-color: #f4f4f4;
}
</style>
