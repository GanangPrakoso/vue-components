<script>
export default {
  emits: ['addCharacter'],

  data() {
    return {
      addName: this.editChar.name,
      addImageUrl: this.editChar.imageUrl
    }
  },
  props: ['page', 'editChar'],
  methods: {
    addCharacter() {
      const newValue = {
        name: this.addName,
        imageUrl: this.addImageUrl
      }
      this.$emit('addCharacter', newValue)
    }
  },
  created() {
    if (this.page === 'add') {
      this.addName = ''
      this.addImageUrl = ''
    }
  }
}
</script>
<!-- lala -->
<template>
  <h1 class="text-center" v-if="page === 'add'">Add Character</h1>
  <h1 class="text-center" v-if="page === 'edit'">Edit Character</h1>

  <div class="container mt-5">
    <form @submit.prevent="addCharacter">
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
      <button type="submit" class="btn btn-primary">Submit</button>
    </form>
  </div>
</template>
