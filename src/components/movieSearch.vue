<template>
  <div class="searchConteiner">
    <h1>Just try Vue.js</h1>
    <div class="searchBox">
    <div class="search">
      <i class="fas fa-search"></i>
      <input type="search" v-model="search" @keydown="callApi()" placeholder="Search ...">
      <select name="" id="" v-model="type" @change="callApi()">
      <option value="" disabled selected>Select type</option>
      <option value="movie">movie</option>
      <option value="series">series</option>
      <option value="eisode">episode</option>
      </select>
    </div> 
    <div class="searchResult">
     <ul>
       <li>
         <p>
           {{item.Error}}
         </p>
       </li>
       <li  v-for=" item in item.Search">
         <img v-bind:src="item.Poster" alt="">
          <p>{{item.Title}}</p>         
       </li>

     </ul>
    </div>
    </div>

  </div>
</template>

<script>
export default {
  name: 'movieSearch',
  data(){
    return{
      item: [],
      search: "",
      type: '',
    }
  },
  beforeCreate(){
    //uradice re nogo sto se bilo sto se desi
  },
  methods:{
    callApi(){
    fetch("http://www.omdbapi.com/?s=" + this.search + "&type=" + this.type+ "&apikey=15ffe88f")
    .then(response => response.json())
    .then((data) => {
      if (data.Response == 'False') {
        this.error = data.Error;
      } else{
        this.error = '';
      }
      this.item = data;
    })
    console.log(this.search)
    },
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
div.searchConteiner{
 padding: 10px 32px 10px 53px;

}
h1{
  text-align: left;
  padding: 0;
  margin: 0;
}
div.search{
    height: 74px;
    background: #1bbc9a;
    margin-top: 17px;
    display: flex;
    align-items: center;
    padding-left: 23px;

}


ul {
  margin: 0;
  list-style-type: none;
  padding: 0;
}
li {
  height: 94px;;
  width: 100%;
  background: #34485d;
  display: inline-block;
  margin: 0;
  display: flex;
  align-items: center;
  border-bottom: 2px solid #2e3e4f;
}
ul li img{
  height: 80px;
}
ul li p{
  color: #fff;
      margin-left: 28px;
}
ul li input{
    margin-left: 31px;
}
a {
  color: #42b983;
}
</style>
