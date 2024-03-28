<script>
export default {
  props: {
    msg: String,
  },
  data() {
    return {
      fact: "John Doe",
      description: "Test Data",
      category: "Going",
      image:"../src/assets/profpic.jpg",
      price:"10.2"
    };
  },
  methods: {
    fetchData() {
      fetch("https://fakestoreapi.com/products/1", {
        method: "GET",
      })
        .then((res) => res.json())
        .then((json) => {
          console.log(json);
          this.fact = json.title;
          this.description = json.description;
          this.category=json.category;
          this.image=json.image;
          this.price=json.price
        })
        .catch((err) => {
          console.error(err);
        });
    },
  },
};
</script>

<template>
  <div class="container">
    <div class="e-card e-card-horizontal">
      <div class="e-card-image"> <img :src="image" style="width:100%;" alt="img"></div>
      <div class="e-card-stacked">
        <div class="e-card-header">
          <!-- <div class="e-card-header-image profile">
           
          </div> -->
          <div class="e-card-header-caption">
            <div class="e-card-title">
              <p v-if="fact">{{ fact }}</p>
            </div>
            <div class="e-card-sub-title">$ {{ price }}</div>
            <div class="e-card-sub-title">{{ category }}</div>
          </div>
        </div>
        <div class="e-card-separator"></div>
        <div class="e-card-content">
          <p v-if="fact">{{ description }}</p>
        </div>
        <div class="e-card-actions e-card-vertical">
          <button @click="fetchData" class="e-card-btn">Get Real Data</button>
          <button class="e-card-btn">Subscribe</button>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-layouts/styles/material.css";
.container {
  margin: 50px auto 0;
  width: 500px;
  height: 700px;
}
.e-card-header-image.profile {
  height: 60px !important;
  width: 60px !important;
}

</style>
