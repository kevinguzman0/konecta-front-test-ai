<template>
  <div>
    <!-- <loading
      v-model="isLoading"
      :can-cancel="false"
      :is-full-page="true"
    /> -->
    <img :src="imagen" class="card-body-img" />
    <h1 class="card-body-title" style="font-size: 2rem">Pokemon {{ id }}</h1>
    <hr />
    
    <h1 class="card-body-title">Abilities</h1>
    <div v-for="todo in todos.abilities" :key="todo.id">
      <p class="card-body-text" >
        {{ todo.ability.name }}
      </p>
    </div>

    <hr />
    <h1 class="card-body-title">Items</h1>
    <div v-for="todo in todos.held_items" :key="todo.id">
      <p class="card-body-text" >
        {{ todo.item.name }}
      </p>
    </div>
    <hr />

    <h1 class="card-body-title">Moves</h1>
    <div v-for="todo in todos.moves" :key="todo.id">
      <p class="card-body-text" >
        {{ todo.move.name }}
      </p>
    </div>
    
  </div>
</template>

<script>
import axios from "axios";

import Loading from "vue-loading-overlay";
import "vue-loading-overlay/dist/vue-loading.css";

export default {
  name: "Pokemon",

  components: {
    Loading,
  },

  data() {
    return {
      isLoading: true,
      todos: null, //Objeto
      imagen: null,
      id: this.$route.params.id,
    };
  },
  mounted() {
    this.isLoading = false;
    this.getTodos();
  },
  methods: {
    async getTodos() {
      await axios
        .get(`https://pokeapi.co/api/v2/pokemon/${this.id}`)
        .then((response) => {
          console.log(response.data);

          this.imagen = response.data.sprites.front_default;

          this.todos = response.data;
        })
        .catch((e) => console.log(e));
    },
  },
};
</script>

<style>

</style>