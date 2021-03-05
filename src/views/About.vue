<template>
  <div class="container">
    <br />
    <b-container class="bv-example-row">
      <b-row>
        <b-col></b-col>
        <b-col>
          <b-img
            :src="toonList.image_url"
            img-alt="Image"
            style="height: 28rem; width: 20rem"
            class="mb-4"
          ></b-img>
        </b-col>
        <b-col></b-col>
      </b-row>
    </b-container>
    <b-card style="background-color: #ccffdd">
      <b-card-title>{{ toonList.title }}</b-card-title>
      <b-card-text> Name English : {{ toonList.title_english }} </b-card-text>
      <b-card-text> Type : {{ toonList.type }} </b-card-text>
      <b-card-text> Chapters : {{ toonList.chapters }} </b-card-text>
      <b-card-text> Synopsis : {{ toonList.synopsis }} </b-card-text>
      <b-card-text class="big text-muted">Last updated 3 mins ago</b-card-text>
    </b-card>
  </div>
</template>


<script>
import axios from "axios";
export default {
  data() {
    return {
      toonList: "",
      url: `https://api.jikan.moe/v3/manga/${this.$route.params.id}`,
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
