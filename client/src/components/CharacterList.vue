<script>
import Card from './Card.vue'
export default {
  components: {
    Card
  },
  props: ['characterList'],
  methods: {
    deleteChar(id) {
      this.$emit('deleteChar', id)
    },
    fetchCharById(id) {
      this.$emit('fetchCharById', id)
    }
  },
  created() {
    this.$emit('fetchCharacter')
  }
}

// reusable => bisa dipake kembali
</script>

<template>
  <div class="container mt-5 d-flex flex-wrap">
    <!-- card -->
    <Card
      @deleteChar="deleteChar"
      @fetchCharById="fetchCharById"
      v-for="(char, index) in characterList"
      :key="char.name"
      :char="char"
    />
    <!-- card -->
  </div>
</template>
