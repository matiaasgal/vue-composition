<script setup>
import {ref, computed} from "vue";
const counter = ref(0);

const increment = () => {
  counter.value++;
};
const decrease = () => {
  counter.value--;
};
const reset = () => {
  counter.value = 0;
};


const numFav = ref([]);
const add = () => {
  numFav.value.push(counter.value)
};

const computedMeth = computed(() => {
  return numFav.value.includes(counter.value);
})

</script>

<template>
<div class="main">
  <div class="container text-center mt-3">
    <h1>Lista de numeros</h1>
    <h2 :class="counter >= 0 ? 'positive' : 'negative' ">{{ counter }}</h2>

    <div class="btn-group">
      <button @click="increment"                      class="btn btn-success">Aumentar</button>
      <button @click="reset"                            class="btn btn-danger">Resetear</button>
      <button @click="decrease"                         class="btn btn-secondary">Disminuir</button>
      <button :disabled="computedMeth" @click="add"     class="btn btn-primary">Favorito</button>
    </div>

    <ul class="list-group mt-2">
      <li v-for="numeros in numFav" class="list-group-item"> {{ numeros }}</li>
    </ul>
  </div>
</div>

</template>



<style scoped>

.positive {
  color: green;
}
.negative {
  color: red;
}

</style>
