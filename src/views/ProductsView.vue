<template>
<div class="container min-vh-100">
<h3>Please login to buy and view products details</h3>
<h1>search</h1>    <button @click="sortPrice">    sort by price    </button>    <input type="text" id="" v-model="search" placeholder="Search">    <select name="" id="" v-model="rating">      <option value="All">All</option>      <option value="electronic devices">Electronic devices</option>      <option value="home appliances">Home appliances</option>  <option value="food">Food</option>  <option value="clothing">Clothing</option><option value="bags">Bags </option>  <option value="home appliances">Liqour</option> Liqour </select>  
<div id="products" class="container h-100 overflow-auto p-4 my-5 gy-5">

<h2 class="fw-bold display-5 text-white">Products</h2>
<h4 class="dispaly"></h4>
<div class="row  justify-content-between gy-2">
<div v-for="product in products" class="col-md-2 card d-flex" :key="product.id">
<div>
  <div class="card-header ">
  <h5 class="card-title mt-0">{{product.title}}</h5>
  <p class="card-text">{{product.category}}</p>
  </div>
  <div class="card-body">
  <img class="img-fluid image m-auto" :src="product.img" :alt="product.title">
    <!-- <p class="card-text description productdesc">{{product.product_description}}</p> -->
    <p class="card-text">R{{product.price}}</p>
    <!-- <router-link :to="{name: 'cart',params:{id:product.product_id}}"> <button class="cart" @click="addToCart">add to cart</button></router-link>
    <router-link :to="{name:'SingleProduct',params:{id:product.product_id}}">
    <button>View</button>
    </router-link> -->
  </div>
</div>
</div>
</div>
</div>
</div>
</template>

<script>

export default {
  data() {
    return {
      search:'',
    }
  },
    computed: {
       products() {
      return this.$store.state.products?.filter(products =>{
          let isMatch = true;
          if (!products.title.toLowerCase().includes(this.search.toLowerCase())) {
              isMatch = false;
          }
          return isMatch
          })
        }
  },
  mounted() {
    this.$store.dispatch('fetchProducts');
  },
  methods: {
    addToCart() {
      const item = {
        title: '',
        category: '',
        product_description: '',
        img: '',
        price: '',
      }
    }
  }
   /*data(){
    return{
      search: ""
    }
  },
  methods: {
    categoty() {
      $this.$store.commit("product.category");
    }
  },
  mounted() {
    this.$store.dispatch('getProducts')
  },
  computed: {
    products() {
      return this.$store.state.products?.filter(product => {
        let isMatch = true;
        if (!product.name.toLowerCase().includes(this.search.toLowerCase())) { isMatch = false } 
      return isMatch
      
    });
    },

  },*/

}


</script>

<style scoped>

.card{
display: flex;
flex-direction: row;
justify-content: center;
flex-wrap: wrap;
color: black;
font-family: San-Francisco;
transition: 0.4s ease-out;
margin-bottom: 10px;
width: 30%;
}
.card:hover {
  box-shadow: rgba(0, 0, 0, 0.22) 0px 19px 43px;
  transform: translate3d(0px, -1px, 0px);
}

img{
  height: 40%px;
}

.productdesc{
    display: flex;
    height: 100%;
    flex-direction: column;
}
</style>
