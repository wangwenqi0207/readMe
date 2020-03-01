<template>
  <div>
     <!-- header部分 -->
    <transition name="slide-down">
      <div class="title-wrapper" v-show="ifTitleAndMenuShow">
      <div class="left">
        <i class="iconfont icon-fanhui icon"></i>
      </div>
      <div class="right">
        <div class="icon-wrapper">
            <span class="iconfont icon-gouwuche icon"></span>
        </div>
        <div class="icon-wrapper">
            <span class="iconfont icon-wode icon"></span>
        </div>
        <div class="icon-wrapper">
            <span class="iconfont icon-gengduo icon"></span>
        </div>
      </div>
    </div>
    </transition>
  </div>
</template>

<script>
export default {
    props:{
        ifTitleAndMenuShow:{
            type:Boolean,
            default:false,
        }    
    },
   methods:{
       
   }
}
</script>

<style lang="scss">
@import '../assets/style/global.scss';
.title-wrapper{
     position: absolute;
     top:0;
     left:0;
     z-index: 101;
     display: flex;
     width:100%;
     height: px2rem(55);
     background: white;
     box-shadow: 0 px2rem(8) px2rem(8) rgba(0,0,0,0.15);
     .left{
        flex:0 0 px2rem(60);
        @include center;
     }
     .right{
       flex:1;
       display: flex;
       justify-content: flex-end;
       .icon-wrapper{
         .icon{
           margin-left: .4rem;
         }
          flex: 0 0 px2rem(40);
          @include center;
          .icon-gouwuche{
            font-size: px2rem(30);
          }
       }
     }
     &.slide-down-enter, &.slide-down-leave-to{
        transform:translate3d(0,-100%,0)
     }
     &.slide-down-enter-to, &.slide-down-leave{
        transform:translate3d(0,0,0)
     }
     &.slide-down-enter-active,&.slide-down-leave-active{
        transition: all .2s linear;
     }
   }
</style>
