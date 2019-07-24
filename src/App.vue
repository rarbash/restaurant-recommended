<template>
  <body>
    <div id="app">
       <div> 
         <h1>What You Think</h1>
        </div>
      <div class="container">
        <div class="row">
        </div><br>
        <h2>Restaurants Name</h2> &nbsp;
        <div class = "searchtab">
          <input class = "searchbox" type="text" v-model="search">&nbsp;&nbsp;&nbsp;<i class="fas fa-search"></i>
        </div>
        <div class = "boxnamerestaurants">
        <div>
         <input class = "inputbox" type="text" name="firstname" v-model="restuarantName" v-on:keyup.enter="addRestuarant()">
          {{ restuarantName }} &nbsp;
          <i class="fas fa-plus-circle botton"></i>  <br><br>
         </div>
       <div class="row restuarantname ">
          <li class="col-md-12 " v-for="rest in restaurants" :key="rest" >
            <div class="restuarantnamebox">
              <span @click="onClickShowModal(rest)"><i class="fas fa-store shopicon "></i>{{ rest }}</span>
              <div>{{starRating}}</div>
              <i class="fas fa-grip-lines-vertical lineicon"></i>
              <div class="dropdown show dotdropdown">
                <a class= "fas fa-ellipsis-v" href="#" role="button" id="dropdownMenuLink" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false"></a>
                <div class="dropdown-menu" aria-labelledby="dropdownMenuLink">
                  <a class="dropdown-item" href="#">Delete</a>
                  <a class="dropdown-item" href="#">Edited</a>
                </div>
              </div>
            </div>
         </li>         
       </div>
     </div>
      <Modal :showModal="showModal" :onClickCloseModal="onClickCloseModal" :titleRestuarant="titleRestuarant"/>
    </div>
    </div>
   </body>
</template>

<script>
import Modal from './components/Modal.vue'

export default {
  name: 'app',
  components: {
    Modal
  },
  data() {
    return{
      restaurants: ['mama' , 'mk' , 'kfc'],
      restuarantName: '',
      showModal: false,
      titleRestuarant: '',
    }
  },
  methods: {
    addRestuarant(){
      console.log( 'hi' , this.restuarantName)
      this.restaurants.push(this.restuarantName)
      this.restuarantName = ''
    },
    onClickShowModal(rest) {
      console.log( "hoo", rest)
      this.titleRestuarant = rest
      this.showModal = true
    },
    onClickCloseModal() {
      this.showModal = false
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: white;
  background-color: #faf2e8;
  height: 100vh;
  
}
  .container {
  padding: 50px;
  
}

  h1 {
    font-size: 70px;
    background-color:  rgb(250 , 143, 141);
    width: 100vw;
    text-align: center;
    padding: 20px;
}
  h2{
    float: left;
    font-size: 40px;
    margin-top: 20px;
    padding-left: 30px;
    padding-top: 10px;
    padding-bottom: 5px;
    width: 400px;
    height: 100px;
    background-color: rgb(250, 143, 141);
    position: absolute;
    border-radius: 10px 25px 1px 1px;
}
  .boxnamerestaurants {
    background-color: #ffdddd;
    color: #534859;
    margin-top: 60px;
    width: 1000px;
    padding: 40px;
    box-shadow: 5px 20px 10px rgba(0, 0, 0, .2);
    position: relative;
    border-radius: 1px 1px 10px 10px;
  }
  .restuarantname {
    font-size: 23px;
  }
  body {
    overflow: hidden;
  }
  .botton{
    color: #5fe1fb;
    font-size: 25px;
  }
  .restuarantnamebox {
    background-color: whitesmoke;
    width: 600px;
    border-radius: 10px;
    display: block;
    padding: 15px;
    display: flex;

  }
  .inputbox,
  .searchbox {
    border-radius: 10px;
    border-style: outset;
    outline: none;
  }

  .searchtab {
    float: right;
    margin-top: 25px;
    margin-right: 40px;
    padding: 20px 0 0 20px;
    width: 235px;
    background-color: rgb(250, 143, 141);
    height: 100px;
    border-radius: 25px 25px 0 0;
  }
  li {
    padding: 10px;
    list-style: none;
  }
  .shopicon {
    padding-right: 10px;
  }
  .lineicon {
    padding-left: 20px;
  }
  .dotdropdown {
     padding-left: 20px;
     color: black; 
  }

  
</style>
