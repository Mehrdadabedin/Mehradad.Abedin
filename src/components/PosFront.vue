<!-- eslint-disable no-unused-vars -->

<template>

  <div class="container" >

    <div class="col1" id="showP" >
      <button class="btn_p"  @click="showButton1 = false"
      
      v-show="showButton1"
     v-for="product in Products" :key="product.id"
       >{{ product.name }}
      </button>
      
  <button  class="btn_menu"  @click="nameP" v-show="!showButton1"
    v-for="pizza in Pizza" :key="pizza.id">
      {{ pizza.name }} 
      <span class="price">{{ pizza.price }}</span>>
    </button>
  
<button class="btn_b" v-if="!showButton1" @click="showButton1=true">Back</button>
</div>
    <div class="col2" >
      <p class="loglabel">Log in for Using POS</p>
      <SideLogin ></SideLogin>
      
      
   
    </div>
    <div class="col3">
      <button id="1" class="btn" @click="name_click">1</button>
      <button id="2" class="btn" @click="name_click">2</button>
      <button id="3" class="btn" @click="name_click">3</button>
      <button id="4" class="btn" @click="name_click">4</button>                                                                                                                                                                                    
      <button id="5" class="btn" @click="name_click">5</button>
      <button id="6" class="btn" @click="name_click">6</button>
      <button id="7" class="btn" @click="name_click">7</button>
      <button id="8" class="btn" @click="name_click">8</button>
      <button id="9" class="btn" @click="name_click">9</button>
      <button id="salg" class="btn" @click="name_click">Payment</button>
      <button id="clr" class="btn">CLR</button>
      
      <button id="0" class="btn">0</button>
      <div class="total" @click="loadJsonFile"></div>
    </div>
  <span>&nbsp;</span>
 <span>
    
    <span><button class="btn2">Admin</button></span>
    <span><button class="btn2">Email</button></span>
    <span><button class="btnonline">Online</button></span>
    <span><button class="btn2">Log out</button></span>
    <span class="logo"><h6> Copyright &copy; 2022 Snapsum</h6></span>
  </span>
   </div>

</template>

<script>
//import json file
import Products from '../assets/Product.json'
import Pizza from '../assets/Pizza.json'  
import SideLogin from './SideLogin.vue'


export default {
  
  name: 'PosFront',
  components: {
  SideLogin
   
  },
  props: {
    msg: String
  },
  data() {
      return {
        data: null,
        buttonValue: '',
        Products, 
        Pizza,
        showDiv : false, 
        btn_pro : true,
        Apears:true,
        showP:true,
        jsonData: null,
        showButton1: true,
        inputValue:''
      
        
      }
    },
    
    
  methods: {
    nameP(event) {
      const buttonText = event.target.innerText;
      window.alert(`You clicked the ${buttonText}!`);
    },
    name_click(event){
      const Salg = event.target.id  
      window.alert(`You clicked ${Salg}!`);  
    },
    mounted() {
  // Check if user is logged in
  if (!this.$store.state.user) {
    // Redirect to login page if user is not logged in
    this.$router.push({ path: '/login' })
  }
}
    
  },
  
  
  //fetch json file into button's btn_p value
  loadData(productId) {
      fetch(`/path/to/product-${productId}.json`)
        .then(response => response.json())
        .then(data => {
          this.buttonValue = data.buttonValue;
      });
    
  },
  loadJsonData () {
    fetch(`../assets/Pizza.json`)
        .then(response => response.json())
        .then(json => {
          this.jsonData = json
        });
    }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
h6 {
  margin-left:0px;
  margin-top:15px;
  font-size: x-large;
  color: rgb(160, 135, 9);
  text-shadow: 3px 1px 1px rgb(40, 32, 8);
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

.container {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  grid-gap: 10px;
  
  color: rgb(33, 24, 24);
  width:100%;
  height:100%;
  margin-top: 0px;
}
.col1 {
  
  color: #000;
  width: 300px;
  height: 100%; 
  border:0px solid rgb(241, 239, 245);  
  border-radius:3px 3px 3px 3px;
}
.col2 {
 background-color: rgb(234, 242, 242);
  color: #000;
  width: 650px;
  height: 100%; 
  border:1px solid rgb(193, 190, 190);  
  border-radius:3px 3px 3px 3px;
}
.col3 {
  
  color: #000;
  width: 350px; 
  height: 100%;
  border:0px solid rgb(129, 131, 128);  
  border-radius:3px 3px 3px 3px;
}
.btn {
  background-color: rgba(12, 12, 12, 0.944);
  color: rgb(245, 235, 190);
  font-size: medium;
  font-weight: bold;
  text-shadow: #5a81a0 0px 0px 0px;
  width: 100px;
  height: 60px;
  border:2px solid rgba(245, 249, 205, 0.4);  
  border-radius:6px 3px 6px 3px;
}

.total {
  background-color:  rgb(248, 248, 248);
  color: #000;
  width: 350px;
  height: 300px;
  border:2px solid  rgb(248, 248, 248);  
  border-radius:3px 3px 3px 3px;
}

.btn_p {
  background-color:rgba(12, 12, 12, 0.944);
  color: rgb(245, 235, 190);
  width: 100px;
  height: 60px;
  font-size: small;
  font-weight: bold;
  border:2px solid rgba(245, 249, 205, 0.4);  
  border-radius:5px 3px 5px 3px;
}

.btn2 {
  background-color: rgba(12, 12, 12, 0.944);
  color:  rgb(245, 235, 190);
  font-size: medium;
  font-weight: bold;
  text-shadow: #096e61 0px 0px 0px;
  width: 100px;
  height: 60px;
  border:2px solid rgba(245, 249, 205, 0.4); 
  border-radius:6px 3px 6px 3px;
}
.btnonline {
  background-color: rgba(12, 12, 12, 0.944);
  color:  rgb(34, 176, 34);
  font-size: medium;
  font-weight: bold;
  text-shadow: #096e61 0px 0px 0px;
  width: 100px;
  height: 60px;
  border:2px solid rgba(245, 249, 205, 0.4); 
  border-radius:6px 3px 6px 3px;
}

.logo {
  background-color: rgb(248, 248, 248);
  color: #000;
  width: 100%;
  height: 50px;
  border:2px solid  rgb(248, 248, 248);  
  border-radius:3px 3px 3px 3px;
  margin-top: 0px;
}
.btn_menu {
  background-color:  rgb(245, 235, 190);
  color: rgba(12, 12, 12, 0.944);
  font-size: medium;
  font-weight: bold;
  text-shadow: #d8e0e6 0px 0px 0px;
  width: 95px;
  height: 60px;
  border:2px solid rgba(98, 94, 94, 0.4);  
  border-radius:6px 3px 6px 3px;
}
.price{
  color: rgb(3, 46, 61) ;
   font-size: small;
  
}

.btn_b {
  background-color: rgba(12, 12, 12, 0.944);
  color: rgb(245, 235, 190);
  font-size: medium;
  font-weight: bold;
  text-shadow: #5a81a0 0px 0px 0px;
  width: 95px;
  height: 60px;
  border:2px solid rgba(245, 249, 205, 0.4); 
  border-radius:6px 3px 6px 3px;
}
.loglabel{
  color: rgb(9, 121, 84) ;
   font-size: large;
   font-weight: bold;
  
}


</style>
