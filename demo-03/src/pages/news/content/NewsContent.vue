<template>
    <div>
      <h1>Content-Page</h1>

      <h2  class="title">{{list.title}}</h2>


      <wxParse :content="list.content" @preview="preview" @navigate="navigate" />

      <!-- <div class="content" v-html="">
       </div>-->
    </div>
</template>

<script>
    import wxParse from 'mpvue-wxparse';
    export default {
      name: "NewsContent",
      components:{
        wxParse
      },
      data(){
        return{
          list:[]
        }
      },
      methods:{

        requestData(aid){

          var that=this;

          var api='http://www.phonegap100.com/appapi.php?a=getPortalArticle&aid='+aid;
          wx.request({
            url: api, //仅为示例，并非真实的接口地址
            header: {
              'content-type': 'application/json' // 默认值
            },
            success: function(res) {
              console.log(res.data);

              that.list=res.data.result[0];
            }
          })

        }
      },
      onLoad: function(options) {

        var aid=options.aid;

        this.requestData(aid);
      }
    }
</script>

<style scoped>
  @import url("~mpvue-wxparse/src/wxParse.css");
</style>
