<template>
    
    <div class="main">
        <h1>
            4chan Auto Board
        </h1>

             <ul class="list-group list-group-flush" stripe >
                 <li class="list-group-item" v-for="thread in threads" :key="thread.posts[0].sub">{{
                     thread.posts[0].sub
                     }} <br> {{thread.posts[0].com}}</li>
            </ul>  

    </div>

</template>

<style>
.posts {
  text-align: left;
}
</style>


<script>
const axios = require("axios");

export default {
  name: "Auto",
  data() {
    return {
      threads: []
    };
  },
  created() {
    axios
      .get("http://a.4cdn.org/o/1.json")
      .then(response => {
        this.threads = response.data.threads;
        console.log(this.threads[0].posts[0].sub);
      })
      .catch(err => {
        console.log(err);
      });
  }
};
</script>
