<template>
  <div>
    <h1>Pokemon {{ id }}</h1>
    <hr />
    <h1>Abilities</h1>
    <div v-for="todo in todos.abilities" :key="todo.id">
      <h2 class="card-body-title">
        {{ todo.ability.name }}
      </h2>
    </div>

    <hr />
    <h1>Items</h1>
    <div v-for="todo in todos.held_items" :key="todo.id">
      <h2 class="card-body-title">
        {{ todo.item.name }}
      </h2>
    </div>
    <hr />

    <h1>Moves</h1>
    <div v-for="todo in todos.moves" :key="todo.id">
      <h2 class="card-body-title">
        {{ todo.move.name }}
      </h2>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "Pokemon",

  data() {
    return {
      todos: null, //Objeto
      imagen: null,
      id: this.$route.params.id,
    };
  },
  mounted() {
    this.getTodos();
  },
  methods: {
    async getTodos() {
      await axios
        .get(`https://pokeapi.co/api/v2/pokemon/${this.id}`)
        .then((response) => {
          console.log(response.data);

          //this.imagen = response.data.sprites.front_default;

          this.todos = response.data;
        })
        .catch((e) => console.log(e));
    },
  },
};
</script>