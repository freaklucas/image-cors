<template>
  <div class="switchableGrid">
    <div class="container">
      <div class="bar">
        <div class="btnHolder">
          <button class="barActive">
            <i class="fa fa-th"></i>
            Grid
          </button>
          <button>
            <i class="fas fa-list"> </i>
            List
          </button>
        </div>
      </div>
      <div class="content">
        <ul class="grid">
          <li v-for="content in contents" :key="content.id">
            <div class="image">
              <img
                :src="content.imageSrc"
              />
            </div>
          </li>
        </ul>
        <ul class="list" v-for="content in contents" :key="content.id">
          <li>
            <img
              :src="content.imageSrc"
            />
            <div class="listContent">
              <h2>{{ content.title }}</h2>
              <p>
                {{ content.description }}
              </p>
              <a class="btn" href="#">Read more</a>
            </div>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>

import axios from 'axios'

export default {
  name: 'Product',
  data() {
    return {
      contents: null,

    }
  },
  mounted() {
    axios
      .get("http://localhost:8080/demo/vue/switchable-grid/api/products.json")
      .then((response) => (this.contents = response.data))
  }
}
</script>