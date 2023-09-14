<script>
export default {
  name: "Card",
  props: ["character"],
  emits: ["deleteChar", "getCharById"],
  methods: {
    deleteChar() {
      this.$emit("deleteChar", this.character.id);
    },

    getCharById() {
      this.$emit("getCharById", this.character.id);
    },
  },
};
</script>

<template>
  <div class="card mx-2 my-2" style="width: 18rem">
    <img class="card-img-top" :src="character.imageUrl" />
    <div class="card-body">
      <h5 class="card-title">{{ character.name }}</h5>
    </div>
    <button class="btn btn-danger" @click="deleteChar">Hapus</button>
    <button class="btn btn-warning" @click="getCharById">Edit</button>
  </div>
</template>

<style></style>
