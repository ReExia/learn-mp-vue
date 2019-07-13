<template>
    <div>
      <h1>User-Page</h1>

      <hr/>
      <ul>
        <li v-for="item in list" :key="key">
          {{item}}
        </li>
      </ul>
    </div>
</template>

<script>
    export default {
        name: "User",
        data(){
          return{
            list:[],
          }
        },

       methods:{
          run(){
            console.log("执行方法");
          }
       },

       created(){
          for (let i = 0 ; i < 10 ; i++) {
            this.list.push("我是第"+i);
          }
       }
    }
</script>

<style scoped>

</style>
