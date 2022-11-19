<template>
  <html>
  <head>
    <title>Vue</title>
    <link rel="stylesheet"
    href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.0-beta1/dist/css/bootstrap.min.css"
    crossorigin="anonymous">
  </head>
  <body>
      <div id="app">
        <main>
          <header>
            <div class="nav navbar-nav navbar-right cart">
              <span class="glyphicon glyphicon-shopping-cart">{{cartItemCount}}</span>
            </div>
          </header>
          <div class="row product">
            <div>
              <figure>
                <img v-bind:src="product.image">
              </figure>
            </div>

            <div class="col col-expand">
              <h1 v-text="product.title"></h1>
              <p v-text="product.description"></p>
              <p class="price">{{product.price | formatPrice}}</p>
              <button v-on:click="addProduct" class="btn" v-if="canAddToCart">Dodaj do koszyka</button>
              <button class="btn--disabled" v-else>Dodajdokoszyka </button>
            </div>
          </div>
        </main>
      </div>
    </body>
</html>
</template>

<script>
export default {
  name: 'MainView',
  data () {
    let product = getProduct()
    return {
      msg: 'vue.js app',
      product: product,
      cart: []
    }
  },
  filters: {
    formatPrice: function (price) {
      return `${price.toLocaleString('pl-PL')} zł`
    }
  },
  methods: {
    addProduct: function () {
      return this.cart.push(this.product.id)
    }
  },
  computed: {
    cartItemCount: function () {
      return this.cart.length || ''
    },
    canAddToCart: function () {
      return this.product.availableInventory > this.cartItemCount
    }
  }
}

const getProduct = () => {
  let product = {
    id: 1001,
    title: 'Worek ziemniaków 10kg',
    description: '10-kilogramowe opakowanie pysznych ziemniaków.',
    price: 1000,
    image: require('./../assets/potato2.jpg'),
    availableInventory: 5
  }
  return product
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.btn {
  width:200px;
  height:50px;
}
</style>
