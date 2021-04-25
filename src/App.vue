<template>
  <div class="container" >
    <h5>List Articles</h5>
    <div class="row row-cols-1 row-cols-md-4">
      <div class="col mb-4" v-for="(article, index) in articles" :key="index">
        <div class="card text-white bg-dark mb-3 h-100  " style="max-width: 18rem;">
          <img :src="selectedImage" class="card-img-top" alt="...">
          <div class="card-body">
            <h5 class="card-title">{{ article.title }}</h5>

          </div>
            <div class="card-footer"> 
            <a :href="article.link" class="btn btn-light btn-block" target="_blank">Visit Website</a>
            </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style>
#app {
  margin-top: 60px;
}
</style>
<script>
import axios from "axios";
export default {
  data() {
    return {
      articles: [],
      selectedImage: 'https://source.unsplash.com/user/erondu/1600x900'
    };
  },

  async mounted() {
    try {
      const res = (await axios.get("http://localhost:5000/api/scrap")).data;
      this.articles = res.data;
    } catch (error) {
      console.error("Error", error);
    }
  },
};
</script>
