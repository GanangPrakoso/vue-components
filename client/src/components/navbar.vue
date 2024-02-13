<script>
// props => passing data dari parent ke child
// emits => passing child ke parent / passing method ke parent

export default {
  props: {
    username: String
  },
  methods: {
    changePage(page) {
      this.$emit('changePage', page)
    }
  }
}
</script>

<template>
  <!-- NAVBAR -->
  <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
    <div class="container-fluid">
      <a class="navbar-brand" @click.prevent="changePage('home')">Ini Navbar</a>

      <div class="d-flex">
        <div></div>
        <div class="d-flex" role="search">
          <a class="navbar-brand">Hi, {{ username }}</a>
          <button class="btn btn-primary mx-3" @click="changePage('add')">Add</button>

          <button class="btn btn-danger">logout</button>
        </div>
      </div>
    </div>
  </nav>
</template>
