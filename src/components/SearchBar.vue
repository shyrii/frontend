<template>
 <div class="form">
        <input type="text" placeholder="搜索感兴趣的商品">
        <div class="search"></div>
</div>
   
</template>

<script>
export default {
  name: "SearchBar",
  methods: {
    
  },
  data(){
      return{
       
      }
  }
};
</script>

<style scoped>
.form {
  height: 50px;
  border-radius: 5px 0px 0px 5px;
  border: none;
  display: flex;
  justify-content: center;
  margin-top: 30px;
}

input {
  width: 650px;
  font-size: 20px;
  padding-left: 8px;
  border:1px solid rgb(229, 229, 229);
}

.search {
  width: 50px;
  height: 50px;
  background-color: rgba(229, 229, 229, 1);
  border-radius: 0px 5px 5px 0px;
  border: none;
  padding: 0;
  background-image: url("../assets/search.svg");
  display: inline-block;
  background-size: 100%;
}

.search:hover{
  cursor: pointer;
  background-color: rgba(255, 195, 0, 1);
  transition-duration: 0.8s;
}
</style>