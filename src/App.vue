<template>
  <div class="d-flex justify-content-center ">
    <div class="">
      <h1 class="mt-5 text-info">Dream BD Cricket Team</h1>
      <h4 class="text-center mt-4">Total Player: {{ playersCount }}</h4>
      <div class="text-center m-4">
        <span v-for="(hero, index) in bdTeam" v-bind:key="hero.name">
          <div>{{ hero.name }} <button type="button" class="close" aria-label="Close" @click="remove(index)"><span aria-hidden="true">&times;</span></button></div>
        </span>
      </div>

      <form class="text-center" @submit.prevent="addPlayer">
        <input class="form-control mb-4" v-model="newHero" placeholder="Player Name Here" />
        <button type="submit"  class="btn btn-outline-success">Add Player</button>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  computed: {
    playersCount() {
      return this.bdTeam.length;
    },
  },

  methods: {
    addPlayer() {
      if (this.newHero !== "") {
        this.bdTeam.push({ name: this.newHero });
        this.newHero = "";
      } else {
        alert("Enter Player Name");
      }
    },
    remove(index) {
      this.bdTeam = this.bdTeam.filter((hero, i) => i != index);
    },
  },

  data() {
    return {
      newHero: "Mamun",

      bdTeam: [
        { name: "Sakib Al Hasan" },
        { name: "Mustafizur Rahman" },
        { name: "Mahmudullah" },
        { name: "Tamim Iqbal" },
      ],
    };
  },
};
</script>

<style>

</style>