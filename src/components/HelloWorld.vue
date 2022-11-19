<template>
  <html>
  <head>
    <title>Vue</title>
    <link rel="stylesheet"
    href=https://cdn.jsdelivr.net/npm/bootstrap@5.0.0-beta1/dist/css/bootstrap.min.css
    crossorigin="anonymous">
  </head>
  <body>
      <div id="app">
        <main>
          <header>
            <div class="navbar navbar-default">
              <h1>xyz</h1>
            </div>
            <div class="nav navbar-nav navbar-right cart">
              <span class="glyphicon glyphicon-shopping-cart" v-text="getCartCount()"></span>
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
              <button v-on:click="addProduct()" style="width:200px"></button>
            </div>
          </div>
        </main>
      </div>
    </body>
</html>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    let product = getProduct()
    return {
      filters: {
        formatPrice: function (price) {
          let fulls = price.toString().slice(0, -2)
          let pennies = price.toString().slice(-2)
          let currency = 'zł'
          return fulls + '.' + pennies + ' ' + currency
        }
      },
      msg: 'vue.js app',
      product: product,
      cart: [],
      addToCart: () => {
        this.cart.push(this.product.id)
      },
      getCartCount: () => {
        return this.cart.length() || ''
      }
    }
  }
}

const getProduct = () => {
  let obj = {
    id: 1,
    title: 'Paczka ziemniaków',
    description: 'ziemniaczki',
    price: 1200,
    image: require('./../assets/potato2.jpg')
  }
  return obj
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
</style>
