<script setup>

import { ref , computed} from "vue";

let counter = ref(0);
const favoritos = ref([]);

const increment = () => {
  counter.value++;
};

const reduce = () => {
  counter.value--;
};

const reset = () => {
  counter.value = 0;
};

const classCounter = computed(() => {
  if(counter.value === 0){
    return "zero"
  }
  if(counter.value > 0){
    return "positive"
  }
  if(counter.value){
    return "negative"
  }
});

const add = () => {
  favoritos.value.push(counter.value);
};

const addButton = computed(() => {
  const numSearch = favoritos.value.find(num => num === counter.value);
  if(numSearch || numSearch === 0){
    return true;
  }
  else{
    return false;
  }
});

</script>


<template>
  <div class="caja">
    <div class="titulo">
      <h1 class="vue">Vue.JS </h1><h1>+</h1><h1 class="bootstrap">Bootstrap</h1>
    </div>
    <div class="titulo">
      <p>By Juan Cruz Genovese</p>
    </div>
    <br>
    <div class="titulo">
      <h2 :class="classCounter"> {{ counter }}</h2>
    </div>   
    <br>
    <div class="d-grid gap-2">
      <button @click="increment" class="btn btn-outline-light btn-lg"> Aumentar</button>
      <button @click="reduce" class="btn btn-outline-light btn-lg"> Reducir </button>
      <button @click="reset" class="btn btn-outline-light btn-lg"> Reset</button>
      <button @click="add" :disabled="addButton" class="btn btn-outline-light btn-lg"> Like </button>
    </div>
    <br>
    <div>
        <h1 class="Fav titulo"> Favoritos </h1> 
      <ul class="list-group">
        <li class="list-group-item list-group-item-secondary" v-for="num in favoritos">
          {{num}}
        </li>
      </ul>
    </div>
    
  </div>
</template> 



<style>

.caja{
  padding-top: 200px;
}
.vue {
  color: rgb(59, 124, 51);
}
.bootstrap {
  color: rgb(109, 73, 143);
}
.titulo{
  display: flex;
  justify-content: center;
}


.positive {
  color: green;
}
.negative{
  color: red;
}
.zero{
  color: grey;
}
</style>