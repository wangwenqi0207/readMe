<template>
  <div class="ebook">
    <title-bar :ifTitleAndMenuShow='ifTitleAndMenuShow'></title-bar>
    <!--电子书  -->
   <div class="read-wrapper">
     <div id='read'></div>
     <!-- 遮罩层 用于控制翻页等按钮 -->
     <div class="mask">
       <div class="left" @click="prevPage"></div>
       <div class="center" @click="toggleTitleAndMenu"></div>
       <div class="right" @click="nextPage"></div>
     </div>
   </div>
   <menu-bar :ifTitleAndMenuShow='ifTitleAndMenuShow' ref="MenuBar"></menu-bar>
  </div>
</template>

<script>
import TitleBar from './components/TitleBar'
import MenuBar from './components/MenuBar'
import Epub from 'epubjs'
const DOWNLOAD_URL = '../static/失控.epub'
global.epub=Epub
export default {
  components:{
      TitleBar,MenuBar
  },
  data(){
      return{
        ifTitleAndMenuShow:false,
      }
  },
   methods:{
      //电子书的解析和渲染
      showEpub(){
        //生成Book
        this.book = new Epub(DOWNLOAD_URL)
        //console.log(this.book)
        //生成Rendition 通过Book.renderTo来生成 read是挂载的dom的id
        this.rendition = this.book.renderTo('read',{
          width:window.innerWidth,
          height:window.innerHeight
        })
        //通过Rendition.display渲染电子书
        this.rendition.display()
      },
      //点击翻上一页
      prevPage(){
        if(this.rendition){
          this.rendition.prev()
        }
      },
      //点击翻下一页
      nextPage(){
        if(this.rendition){
          this.rendition.next()
        }
      },
      toggleTitleAndMenu(){
        this.ifTitleAndMenuShow = !this.ifTitleAndMenuShow;
        //点击屏幕中间设置按钮取消
        if(!this.ifTitleAndMenuShow){
            this.$refs.MenuBar.HideSetting()
        }
      }
   },
   mounted(){
     this.showEpub()
   }
}
</script>

<style lang="scss">
@import 'assets/style/global.scss';
.ebook{
   position: relative;
   background: #f8d8a7;
   
   .read-wrapper{
     .mask{
       position:absolute;
       top:0;
       left:0;
       z-index:100;
       width: 100%;
       height: 100%;
       display: flex;
       .left{
          flex: 0 0 px2rem(100);
          // background: yellow;
       }
       .center{
          flex:1;
          // background: red;
       }
       .right{
           flex: 0 0 px2rem(100);
          //  background: green;
       }
     }
   }
}

</style>
