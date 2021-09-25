<template>
  <div class="flex" style="align-items: center">
    <article class="card">
      <img
        src="../assets/images/bg-pattern-card.svg"
        alt="imagen header card"
        class="card-header"
      />
      <div class="card-body">
        <Pokemon />
      </div>
    </article>
  </div>
</template>

<script>
import Pokemon from "../components/Pokemon.vue";

export default {
  components: {
    Pokemon,
  },
};
</script>
