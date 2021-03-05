<template>
  <div>
    <br />
    <b-card
      :img-src="Img"
      img-alt="Image"
      img-top
      border-variant="dark"
      tag="article"
      style="height: 23rem; width: 10rem; background-color: #b3d1ff"
      class="mb-2"
    >
      <router-link :to="`/about/${this.id}`">
        <b-card-text>
          <h6 class="text-dark ">{{ name }}</h6>
        </b-card-text>
      </router-link>
    </b-card>
  </div>
</template>

<script>
export default {
  props: {
    id: Number,
    name: String,
    Img: String,
  },
};
</script>

<style>
</style>