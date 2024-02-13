<script>
// 1. klik button
// 2. fetch data by id
// 3. udah dapet data => pindah page (udpate state page)
// 4. populate data ke form

export default {
  props: ['char'],
  methods: {
    deleteChar() {
      this.$emit('deleteChar', this.char.id)
    },
    fetchCharById() {
      this.$emit('fetchCharById', this.char.id)
    }
  }
}
</script>

<template>
  <div class="card mx-2 my-2" style="width: 18rem">
    <img class="card-img-top" :src="char.imageUrl" />
    <div class="card-body">
      <h5 class="card-title">{{ char.name }}</h5>
      <button class="btn btn-danger" @click="deleteChar">Delete</button>
      <button class="btn btn-success ms-2" @click="fetchCharById">Edit</button>
    </div>
  </div>
</template>
