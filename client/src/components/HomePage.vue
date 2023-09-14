<script>
import CharacterCard from "./CharacterCard.vue";

export default {
  emits: ["fetchCharacters", "deleteChar", "getCharById"],
  components: {
    CharacterCard,
  },
  props: ["characterList"],
  methods: {
    deleteChar(id) {
      this.$emit("deleteChar", id);
    },

    getCharById(id) {
      this.$emit("getCharById", id);
    },
  },
  created() {
    this.$emit("fetchCharacters");
  },
};
</script>

<template>
  <div class="container pt-3">
    <div class="text-center">
      <h1>home page</h1>
    </div>
    <!-- TABLE -->
    <div class="container d-flex flex-wrap">
      <!-- Table row -->
      <CharacterCard
        v-for="character in characterList"
        :key="character.id"
        :character="character"
        @deleteChar="deleteChar"
        @getCharById="getCharById"
      />
      <!-- card -->
    </div>
  </div>
</template>
