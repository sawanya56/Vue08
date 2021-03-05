<template>
  <div id="app" style="background-image:url('https://wallpaperaccess.com/full/21614.jpg')">
    <b-navbar toggleable="lg" class="a">
      <router-link :to="'/'">
        <b-iconstack font-scale="3" class="mr-3">
          <b-icon stacked icon="book" variant="white"></b-icon>
        </b-iconstack>
        <b-navbar-brand class="text-white"><h2>MANGA</h2></b-navbar-brand>
      </router-link>
      <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

      <b-collapse id="nav-collapse" is-nav>
        <!-- Right aligned nav items -->
        <b-navbar-nav class="ml-auto">
          <b-nav-form>
            <b-form-input
              size="sm"
              class="mr-sm-2"
              placeholder="Search"
              v-model="sh"
            ></b-form-input>
            <b-button
              variant="outline-light"
              class="my-2 my-sm-0"
              type="submit"
              @click="search"
              >Search</b-button
            >
          </b-nav-form>
        </b-navbar-nav>
      </b-collapse>
    </b-navbar>

    <router-view />
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      sh: "",
      mangaList: "",
      url: "https://api.jikan.moe/v3/magazine/1/1",
    };
  },
  methods: {
    search() {
      const router = this.$router;
      for (let i = 0; i <= this.mangaList.manga.length; i++) {
        if (this.sh == this.mangaList.manga[i].title) {
          alert(this.mangaList.manga[i].title);
          router.push({
            path: `/about/${this.mangaList.manga[i].mal_id}`,
          });
          break;
        } else if (99 == i) {
          alert("Not listed!!!");
          router.push({
            path: `/`,
          });
        }
      }
    },
  },
  mounted() {
    axios
      .get(this.url)
      .then((response) => {
        this.mangaList = response.data;
      })
      .catch((err) => {
        console.log(err);
      });
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
.a {
  background-color: blueviolet;
}
</style>
