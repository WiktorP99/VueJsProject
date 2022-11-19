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
          <div class="row product">
            <div>
              <figure>
                <img v-bind:src="product.image">
              </figure>
            </div>

            <div class="col col-expand">
              <h1 v-text="product.title"></h1>
              <p v-text="product.description"></p>
              <p v-text="product.price" class="price"></p>
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
    var product = getProuct()
    return {
      filters: {
        formatPrice: function(price) {
          
        }
      },
      msg: 'Welcome to Your Vue.js App',
      product: product
    }
  }
}

const getProuct = () => {
  var obj = {
    id: 1001,
    title: 'Worek ziemniaków',
    description: '10-kilogramoweopakowaniepysznychziemniaków',
    price: 1000,
    image: require('C://STUDIA/projekt1/src/assets/potato2.jpg')
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
