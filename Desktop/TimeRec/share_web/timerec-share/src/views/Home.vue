<template>
  <div class="home">
      <div class="user-content">
          <li v-for="post in this.content" v-text="post"></li>
      </div>
  </div>
</template>

<script>
  import Axios from "axios";
  export default {
    name: 'Home',
    components: {
    },
    data(){
      return{
          content: null
      }
    },
    methods: {
      getData(){
          let api = 'http://api.mytimerec.com/api/capsule/index_data/2?pageIndex=0';
          Axios.get(api).then((response) => {
              this.content = response.data.data.rows;
          }).catch((error)=>{
              console.log(error)
          })
      }
    },
    mounted() {
      this.getData();
    }
  }
</script>

<style lang="scss">
  $border-color: #e0e0da;
  home {
      color: black;
      position: relative;
  }
  .user-content{
      padding: 2rem;
      margin: auto;
  }
</style>
