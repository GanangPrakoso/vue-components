<script>
export default {
  name: "Card",
  props: ["character"],
};
</script>

<template>
  <div class="card mx-2 my-2" style="width: 18rem">
    <img class="card-img-top" :src="character.imageUrl" />
    <div class="card-body">
      <h5 class="card-title">{{ character.name }}</h5>
    </div>
  </div>
</template>

<style></style>
