<template>
  <div>
    <table>
      <tbody>
        <img
          src="https://raw.githubusercontent.com/PokeAPI/media/master/logo/pokeapi_256.png"
          alt=""
          class="responsive"
        />
        <tr v-for="todo in todos" :key="todo.id">
          <td>
            <router-link :to="{ name: 'Details', params: { id: todo.name } }">
              <article class="card" style="margin-top: 10px">
                <h1 class="card-body-title">
                  {{ todo.name }}
                </h1>
              </article>
            </router-link>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "Cards",
  
  data() {
    return {     
      todos: null, //Objeto
    };
  },
  
  mounted() {
    this.getTodos();
    
  },
  methods: {
    async getTodos() {
      //await axios.get(`https://pokeapi.co/api/v2/pokemon/${id}`)
      await axios
        .get("https://pokeapi.co/api/v2/pokemon?limit=50&offset=10")
        .then((response) => {
          console.log(response);
          this.todos = response.data.results;
        })
        .catch((e) => console.log(e));
    },
  },
};
</script>

<style>
.responsive {
  width: 100%;
  height: auto;
}
a {
  color: black;
  text-transform: capitalize;
  text-decoration: none;
}
</style>