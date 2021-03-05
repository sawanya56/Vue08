<template>
  <div class="container">
    <div class="row justify-content-center">
      <HelloWorld
        class="col-2"
        v-for="(item, index) in toonList.manga"
        :key="index"
        :name="item.title"
        :Img="item.image_url"
        :id="item.mal_id"
      />
    </div>
  </div>
</template>

<script>
import axios from "axios";
import HelloWorld from "../components/HelloWorld.vue";

export default {
  components: { HelloWorld },
  data() {
    return {
      toonList: "",
      url: "https://api.jikan.moe/v3/magazine/1/1",
    };
  },
  mounted() {
    axios
      .get(this.url)
      .then((response) => {
        this.toonList = response.data;
      })
      .catch((err) => {
        console.log(err);
      });
  },
  
};
</script>
