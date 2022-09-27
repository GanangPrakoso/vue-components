<script>
export default {
  name: "NavbarCustom",
  props: ["username"],
};
</script>

<template>
  <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
    <div class="container-fluid">
      <a class="navbar-brand">Ini Navbar</a>

      <div class="d-flex">
        <div></div>
        <div class="d-flex" role="search">
          <a class="navbar-brand">Hi, {{ username }}</a>

          <button class="btn btn-danger">logout</button>
        </div>
      </div>
    </div>
  </nav>
</template>
