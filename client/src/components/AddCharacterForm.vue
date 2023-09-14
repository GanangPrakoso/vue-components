<script>
export default {
  props: ["detailData", "page"],
  emits: ["addCharacter"],
  data() {
    return {
      addName: "",
      addImageUrl: "",
    };
  },

  methods: {
    submitHandler() {
      if (this.page === "add") {
        const value = {
          name: this.addName,
          imageUrl: this.addImageUrl,
        };

        this.$emit("addCharacter", value);
      } else {
        // nge emit method untuk edit
      }
    },
  },

  created() {
    if (this.detailData && this.page === "edit") {
      this.addName = this.detailData.name;
      this.addImageUrl = this.detailData.imageUrl;
    }
  },
};
</script>

<template>
  <div class="container mt-5">
    <h1 v-if="page === 'add'">Add Character</h1>
    <h1 v-if="page === 'edit'">Edit Character</h1>
    <form @submit.prevent="submitHandler">
      <div class="form-group my-2">
        <label>Name</label>
        <input
          type="text"
          class="form-control"
          placeholder="Enter character name"
          v-model="addName"
        />
      </div>
      <div class="form-group my-2">
        <label>Image url</label>
        <input
          type="text"
          class="form-control"
          placeholder="Enter character image url"
          v-model="addImageUrl"
        />
      </div>
      <button type="submit" class="btn btn-primary">Add Character</button>
    </form>
  </div>
</template>
