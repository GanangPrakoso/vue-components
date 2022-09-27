<!-- menuliskan js (vue) -->
<script>
import axios from "axios";
import Navbar from "./components/Navbar.vue";
import CharacterCard from "./components/CharacterCard.vue";
import AddCharacterForm from "./components/AddCharacterForm.vue";

export default {
  components: {
    Navbar,
    CharacterCard,
    AddCharacterForm,
  },
  data() {
    return {
      baseUrl: "http://localhost:3000",
      username: "Dadang Konelo",
      characterList: [],
    };
  },
  methods: {
    async fetchCharacters() {
      try {
        const { data } = await axios({
          method: "get",
          url: this.baseUrl + "/characters",
        });

        this.characterList = data;
      } catch (err) {
        console.log(err);
      }
    },

    async addCharacter(value) {
      try {
        console.log(value);
        await axios({
          url: this.baseUrl + "/characters",
          method: "post",
          data: {
            name: value.name,
            imageUrl: value.imageUrl,
          },
        });
        this.fetchCharacters();
      } catch (err) {
        console.log(err);
      }
    },
  },

  created() {
    this.fetchCharacters();
  },
};
</script>

<!-- menuliskan HTML -->
<template>
  <!-- component = tag html yang baru -->

  <!-- NAVBAR -->
  <Navbar :username="username" />

  <!-- ADD CHARACTER -->
  <AddCharacterForm @addCharacter="addCharacter" />
  <!-- CHARACTERS LIST -->
  <div class="container mt-5 d-flex flex-wrap">
    <!-- card -->
    <CharacterCard
      v-for="character in characterList"
      :key="character.id"
      :character="character"
    />
    <!-- card -->
  </div>
</template>

<!-- menuliskan CSS / styling -->
<style></style>
