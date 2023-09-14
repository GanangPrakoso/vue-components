<!-- menuliskan js (vue) -->
<script>
import axios from "axios";
import Navbar from "./components/Navbar.vue";
import CharacterCard from "./components/CharacterCard.vue";
import AddCharacterForm from "./components/AddCharacterForm.vue";
import Home from "./components/HomePage.vue";

export default {
  components: {
    Navbar,
    CharacterCard,
    AddCharacterForm,
    Home,
  },
  data() {
    return {
      baseUrl: "http://localhost:3000",
      username: "Dadang Konelo",
      characterList: [],
      page: "home",
      detailData: {},
    };
  },
  methods: {
    changePage(page) {
      this.page = page;
    },

    async getCharById(id) {
      try {
        const { data } = await axios({
          url: this.baseUrl + "/characters/" + id,
          method: "get",
        });

        this.detailData = data;

        this.changePage("edit");
      } catch (error) {
        console.log(error);
      }
    },

    async fetchCharacters() {
      try {
        const { data } = await axios({
          method: "get",
          url: this.baseUrl + "/characters",
        });

        console.log(data, "<<<<<");
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

        // this.changePage("home");
        cb();
      } catch (err) {
        console.log(err);
      }
    },

    async deleteChar(id) {
      try {
        await axios({
          url: this.baseUrl + "/characters/" + id,
          method: "delete",
        });
        this.fetchCharacters();
      } catch (error) {
        console.log(error);
      }
    },
  },

  created() {
    // this.fetchCharacters();
  },
};
</script>

<!-- menuliskan HTML -->
<template>
  <!-- component = tag html yang baru -->

  <!-- NAVBAR -->
  <Navbar :username="username" @changePage="changePage" />

  <!-- ADD CHARACTER -->
  <AddCharacterForm
    v-if="page === 'add'"
    @addCharacter="addCharacter"
    :page="page"
  />

  <AddCharacterForm
    v-if="page === 'edit'"
    :detailData="detailData"
    :page="page"
  />

  <!-- CHARACTERS LIST -->
  <Home
    v-if="page === 'home'"
    :characterList="characterList"
    @fetchCharacters="fetchCharacters"
    @deleteChar="deleteChar"
    @getCharById="getCharById"
  />
</template>

<!-- menuliskan CSS / styling -->
<style></style>
