<script setup >
  const name = 'Vue dinamico'
  // const styleColor = "color: blue"
  // const arrayColores = ["blue", "red", "chartreuse"];
  // const active = true
  // const active3 = false
  // const activo = null
  // const active2 = false
  // const arrayFrutas = ["🍎", "🍌", "🍉", "🍓", "🍒"];
  // const arrayFrutas2 = [
  // {
  //       name: "Manzana",
  //       price: "$1.00",
  //       description: "Una manzana",
  //       stock: 0,
  //   },
  //   {
  //       name: "Pera",
  //       price: "$2.00",
  //       description: "Una pera",
  //       stock: 10,
  //   },
  //   {
  //       name: "Naranja",
  //       price: "$3.00",
  //       description: "Una naranja",
  //       stock: 20,
  //   },
  // ]
  // const arrayWaifuGI = [
  //   {
  //     name: "Ganyu",
  //     elemento: "Crio",
  //     description: "Es una arquera con cuernos de la raza adeptus"
  //   },
  //   {
  //     name: "Xianyun",
  //     elemento: "Anemo",
  //     description: "Es un personaje de catalizador y ella es considerada como la preservadora de la nubes"
  //   },
  //   {
  //     name: "Yoimiya",
  //     elemento: "Pyro",
  //     description: "Es un personaje de arco, es muy energica, alegre, le gusta ayudar a los demas y se encarga de crear fuegos artificiales"
  //   }
  // ]
  // const objetoFruta = {
  //   name: "Manzana",
  //   price: "$1.00",
  //   description: "Es una fruta",
  //   id: 1,
  // }
//   const users = [
//   {
//     id: 1,
//     name: 'Juan',
//     posts: [
//       { id: 1, title: 'Mi primer post' },
//       { id: 2, title: 'Mi segundo post' },
//     ]
//   },
//   {
//     id: 2,
//     name: 'Maria',
//     posts: [
//       { id: 3, title: 'Mi tercer post' },
//       { id: 4, title: 'Mi cuarto post' },
//     ]
//   }
// ]
// metodo - methods
//const dameClick = (message) => {
//  console.log(message)
//}
import { ref, computed } from "vue";

const counter = ref(0)
const arrayCounter = ref([])
// const arrayColores = ["green", "red"]

const increment = () => {
  // console.log('aumentar contador')
  counter.value++
  // console.log(counter);
}
const decrementar = () => {
  // console.log('aumentar contador')
  counter.value--
  // console.log(counter);
}
 const borrar = () => {
  counter.value = 0
}

 const add = () => {
  arrayCounter.value.push(counter.value)
 }

const blockNumber = computed(() => {
    const number = arrayCounter.value.find((num) => num === counter.value);
    return number || number === 0;
});

const classCounter = computed(() => {
    if (counter.value === 0) {
        return "zero";
    }
    return counter.value > 0 ? "positive" : "negative";
});

</script>

<template>
      <!-- <ul>
        <li v-if="counter >= 0">
          <h2 v-bind:style="`color: ${arrayColores[0]}`">{{ counter }}</h2>
        </li>
        <li v-else-if="counter < 0">
          <h2 v-bind:style="`color: ${arrayColores[1]}`">{{ counter }}</h2>
        </li>
      </ul> -->
      <!-- <h2 :class="counter >= 0 ? 'positive' : 'negative'">
        {{ counter }}
      </h2> -->
    <div class="container text-center">
      <h1> CONTANDOR {{ name.toUpperCase() }}</h1>
    </div>

      <br>
      <h2 :class="classCounter" style="text-align: center;">
        {{ counter }}
      </h2>
      <br>

    <div class="btn-group">
      <button @click="increment" class="btn btn-success">Aumentar</button>
      <br>
      <button @click="decrementar" class="btn btn-danger">Decrementar</button>
      <br>
      <button @click="borrar" class="btn btn-secondary">Receptear</button>
      <br>
      <button @click="add" :disabled="blockNumber" class="btn btn-primary">Add</button>
    </div>
      <br>
      <ul class="list-group mt-4 container text-center">
        <li class="list-group-item" v-for="(item, index) in arrayCounter" :key="index">
            {{ item }}
        </li>
      </ul>
    <!-- <h1> La vida de un crítico es sencilla en muchos aspectos, arriesgamos poco, y tenemos poder sobre aquellos que ofrecen su trabajo y su servicio a nuestro juicio. </h1>
    <br> -->
    <!-- <div>
      <h2>Lista de usuarios:</h2>
      <ul>
        <template 
        v-for="(user, index) in users"
        :key="user.id"
        >
        <li>
          <h3>{{ user.name }}</h3>
          <ul>
            <template
            v-for="(post, index) in user.posts"
            :key="post.id"
            >
            <li>{{ post.title }}</li>
            </template>
          </ul>
        </li>
        </template>
      </ul>
    </div> -->
    <!-- <br>
    <button v-on:click="dameClick('Texto 1')">Activame ya</button>
    <button @click="dameClick('Texto 2')">Activame ya</button>
    <button v-on:click.right.prevent="dameClick('Texto right')"> A perro traes el omitriz</button>
    <button v-on:click.middle="dameClick('Texto middle')"> Que pa soooo</button>
    <button v-on:click.left="dameClick('Texto left')"> Vamos a calmano</button> -->

    <!-- <h2>{{ arrayColores }}</h2>
    <br>
    <h3 v-bind:style="styleColor"> Atte : Ego(Critico de Ratatouille)</h3>
    <br>
    <h3 v-bind:style="`color: ${arrayColores[2]}`"> Critico experto</h3>
    <br>
    <h3>{{ name.toUpperCase() }}</h3>
    <br>
    <h3>
      {{ active ? 'Estoy activo' : 'Estoy inactivo' }}
    </h3> -->
    <!-- <br>
    <p v-if="!active">No estes chingando</p>
    <br>
    <p v-if="active">!!!QUE QUIERES!!!</p>
    <p v-else>!!!NO ME MOLESTES</p>
    <br>
    <p v-if="activo === true"> "ESTOOOY AQUI LA MADRE QUE TE APARIO"</p>
    <p v-else-if="activo === false">"ME VOY ESTOY ARTO DE TI"</p>
    <p v-else> Sabes que no, no me haz pagado XD</p> -->
    <!-- <br>
    <h2 v-show="active2">soy invisible</h2>
    <br>
    <ul>
        <li v-for="(fruta, index) in arrayFrutas" :key="index">
           {{ index }} - {{ fruta }}
        </li>
    </ul>
    <br>
    <p> </p>
    <br>
    <ul>
      <li v-for="(waifu, id) in arrayWaifuGI" :key="id">
        {{ waifu.id }} - {{ waifu.name }} - {{ waifu.elemento }} - {{ waifu.description }}
      </li>
    </ul>
    <br>
    <p> </p>
    <br>
    <ul>
      <li v-for="(value, propiedad, index) in objetoFruta" :key="value">
       {{ index }} : {{ propiedad }} : {{ value }}
      </li>
    </ul>
    <br> -->
    <!-- <ul>
      <li  
      v-for="item in arrayFrutas2" 
      :key="item.name" >
        {{ item.name }} - {{ item.price }}
      </li>
    </ul> -->
    <!-- <ul>

      <li v-for="item in arrayFrutas2" :key="item.name">
        <span v-if="item.stock > 0">
          {{ item.name }} - {{ item.price }}
        </span>

      </li>
    </ul>
    <br>
    <p> </p>
    <br>
    <ul>
      <template v-for="item in arrayFrutas2" :key="item.name">
        <li v-if="item.stock > 0">
          {{ item.name }} - {{ item.price }}
        </li>
      </template>
    </ul> -->
    <!-- {{ objetoFruta }} -->
    
</template>

<style>
  h1 {
    color: chartreuse;
  }
  .negative {
    color: red;
  }

  .positive {
    color: green;
  }
  .zero {
    color: black; 
  }
</style>