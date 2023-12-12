<template>
  <div class="search">
    <input type="search" v-model="search">
  </div>
  <div class="dropdown">
    <select value="classic" v-model="dropdown">
      <!-- <option disabled selected hidden>Category</option> -->
      <option value="classic">Classic</option>
      <option value="modern">Modern</option>
    </select>
  </div>
  <ul>
  </ul>
  <div class="items">
    <div class="card" v-for="product in categorisedProducts()" :key="product.make">
      <div class="card-header">
        <h2>{{ product.name }}</h2>
      </div>
      <div class="cardbody">
        <img :src="product.img" :alt="product.name">
        <p>{{ product.make }}</p>
        <p>{{ product.description }}</p>
        <p>{{ product.price }}</p>
      </div>
      <div class="card-footer"></div>
    </div>
  </div>
</template>

<script>


export default {
  name: 'App',
  components: {},
  data() {
    return {
      search: '',
      dropdown: '',
      products: [
        {
          name: "classic black tuxedo",
          make: "The Satin Lapel",
          description: "A full classic tuxedo, complete with shirt, bowtie, pants and shoe style of your choice",
          price: 5000,
          img: "https://i.postimg.cc/TfGL5hDn/Screenshot-2023-12-02-215612.jpg",
          category: 'classic'
        },
        {
          name: "satin lapeled navy tux",
          make: "The Satin Lapel",
          description: "A full navy tuxedo with custom satin lapels, complete with shirt, bowtie/tie, pants and shoe style of your choice",
          price: 6000,
          img: "https://i.postimg.cc/JM47WXXY/Screenshot-2023-12-02-220048.jpg",
          category: 'classic'
        },
        {
          name: "satin lapeled grey tux",
          make: "The Satin Lapel",
          description: "A full grey tuxedo with custom satin lapels, complete with shirt, bowtie/tie, pants and shoe style of your choice",
          price: 5000,
          img: "https://i.postimg.cc/fzcWMj5p/Screenshot-2023-12-02-220013.jpg",
          category: 'modern'
        },
        {
          name: "satin lapeled silver tux",
          make: "The Satin Lapel",
          description: "A full silver tuxedo with custom satin lapels, complete with shirt, bowtie, pants and shoe style of your choice",
          price: 7000,
          img: "https://i.postimg.cc/yxnY6sHv/Screenshot-2023-12-02-215521.jpg",
          category: 'modern'
        },
      ]
    }
  },

  methods: {
    categorisedProducts(){
      if (this.dropdown == 'classic'){
        if (this.search.length > 0) {
          return this.classic.filter(item => {
            return item.name.toLocaleLowerCase().includes(this.search.toLowerCase())
          })
        }
        return this.classic
      } else if (this.dropdown == 'modern'){
        if (this.search.length > 0) {
          return this.modern.filter(item => {
            return item.name.toLocaleLowerCase().includes(this.search.toLowerCase())
          })
        }
        return this.modern
      }
    }
  },

  computed: {
    classic() {
      return this.products.filter(item => item.category.toLowerCase() ==('classic') )
    },
    modern() {
      return this.products.filter(item => item.category.toLowerCase() ==('modern') )
    },
  },
}
</script>

<style>
#app {
  height: 100%;
  width: 100%;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

img {
  height: 300px;
  width: 200px;
  object-fit: cover;
}

.dropdown {
  position: relative;
  display: inline-block;
}

.dropdown-content {
  display: none;
  position: absolute;
  background-color: #f9f9f9;
  min-width: 160px;
  box-shadow: 0px 8px 16px 0px rgba(0, 0, 0, 0.2);
  padding: 12px 16px;
  z-index: 1;
}

.dropdown:hover .dropdown-content {
  display: block;
}
</style>
