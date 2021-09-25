<template>
    <div class="flex">
        <article class="card">
          <div class="card-body">
            <Pokemon />
          </div>
        </article>
        
    </div>
</template>

<script>

import Pokemon from "../components/Pokemon.vue"

export default {
  components: {
    Pokemon
  }
};
</script>
