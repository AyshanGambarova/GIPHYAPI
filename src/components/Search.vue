<template>
  <div class="search">
    <input type="text" v-model="query" @keydown.enter='handleSearch' placeholder="Enter your GIF..."/>
  </div>
</template>

<script>
export default {
    data(){
        return{
            query:''
        }
    },
    methods:{
        handleSearch(){
            this.$emit('search',this.query);
            this.query=''
        }
    }
}
</script>
<style>
.search{
    display: flex;
    justify-content: center;
    width: 100%;
    margin-top: 15px;
}
.search input{
    padding: 10px 20px;
    border: 1px solid #CCC;
    border-radius: 5px;
    width: 400px;
}
.search input:focus{
   outline-color: pink;
}
.search button{
    padding: 10px 20px;
    border: 1px solid #CCC;
    background-color: rgb(127, 127, 199);
    color: white;
      border-radius: 5px;
}
</style>