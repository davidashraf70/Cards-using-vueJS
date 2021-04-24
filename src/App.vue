<template>
  <main id="app" @mousemove="mousemove">
    <section class="products">
      <product 
      v-for="product in products"
      :key="product.color"
      :product="product"
      />
    </section>
    <router-view />
  </main>
</template>

<script>
import product from './components/product.vue';
export default {
  name:'app',
  components:{
    product,
  },
  data(){
    return{
      products:[
        {
          title:'Nike Air Max',
          color:'red',
          bgtext:'NIKE',
          src: require('./assets/one.png')
        },
        {
          title:'Nike flex',
          color:'blue',
          bgtext:'AIR',
          src: require('./assets/two.png')
        },
        {
          title:'Nike Roche Runs',
          color:'gray',
          bgtext:'MAX',
          src: require('./assets/three.png')
        }
      ]
    }
  },
  methods:{
    mousemove(e){
      let mouseX = e.clientX;
      let mouseY = e.clientY;

      let products = document.querySelectorAll('.products .product');


      for(let i=0; i < products.length; i++){

        let product = products[i];

        let product_image = product.querySelector('.product-image-wrap');

        let img_x = mouseX - this.coords(product_image).x;
        let img_y = mouseY - this.coords(product_image).y;
        product_image.style.transform = `translateY(-${img_y/40}px) translateX(-${img_x/40}px) translateZ(100px)`;

        let bgtext = product.querySelector('.bg-text');
        let bg_x = mouseX - this.coords(bgtext).x;
        bgtext.style.transform = `translateX(${bg_x/25}px)`;
      }
    },
    coords(el){
      let coords = el.getBoundingClientRect();

      return{
        x: coords.left /2,
        y: coords.top /2
      }
    }
  }
}
</script>

<style lang="scss" scoped>
*{
  margin: 0px;
  padding: 0px;
  box-sizing: border-box;
}
body{
  font-family:'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
  main{
    width: 100vw;
    min-height: 100vh;
    overflow: hidden;
    background-color:#EEE;

    display: flex;
    justify-content: center; 
    align-items: center;
    .products{
      display: flex;
      max-width: 1200px;
      padding: 25px;
      margin: 0 auto;
    }
  }
}
</style>
