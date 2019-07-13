<template>

  <div>
    <h1>Page-News</h1>
    <ul class="list">
      <li v-for="(item,key) in list" :key="key">

        {{item.title}}
      </li>
    </ul>
  </div>
</template>

<script>
  export default {
    name: "News",

    data() {
      return {
        list:[]
      }
    },

    methods: {
      requestData(){

        var that=this;

        var api='http://www.phonegap100.com/appapi.php';

        wx.request({
          url: api, //仅为示例，并非真实的接口地址
          data: {
            a: 'getPortalList' ,
            catid: '20',
            page:'1'
          },
          header: {
            'content-type': 'application/json' // 默认值
          },
          success: function(res) {
            // console.log(res.data)

            that.list=res.data.result;
          }
        })
      }
    },

    created() {
      this.requestData();
    },
  }
</script>

<style scoped>

</style>
