<script>
export default {
  emits: ["addCharacter"],
  data() {
    return {
      addName: "",
      addImageUrl: "",
    };
  },

  methods: {
    submitHandler() {
      const value = {
        name: this.addName,
        imageUrl: this.addImageUrl,
      };

      this.$emit("addCharacter", value);
    },
  },
};
</script>

<template>
  <div class="container mt-5">
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
