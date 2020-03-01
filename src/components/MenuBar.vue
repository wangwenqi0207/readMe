<template>
  <div>
     <!-- 底部菜单 -->
       <div class="menu-bar">
        <transition name="slide-up">
        <div class="menu-wrapper" v-show="ifTitleAndMenuShow" :class="{'hide-box-shadow':ifSettingShow  || !ifTitleAndMenuShow}">
            <div class="icon-wrapper">
                <span class="iconfont icon-caidan-dakai icon"></span>
            </div>
        <div class="icon-wrapper">
            <span class="iconfont icon-icon-test icon"></span>
        </div>
        <div class="icon-wrapper">
            <span class="iconfont icon-baitianmoshimingliangmoshi icon"></span>
         </div>
        <div class="icon-wrapper">
            <span class="iconfont icon" @click="ShowSetting">A</span>
        </div>
        </div>
         </transition>
          <!-- 点击设置 -->
          <transition name="slide-up">
            <div class="setting-wrapper" v-show="ifSettingShow">
            <!-- 字号设置 -->
                <div class="setting-font-size">
                    
                </div>
            </div>
        </transition>
       </div>
  </div>
</template>

<script>
export default {
    data(){
        return{
            ifSettingShow:false,
        }
    },
     props:{
        ifTitleAndMenuShow:{
            type:Boolean,
            default:false,
        }    
    },
    methods:{
        //点击A字设置出现
        ShowSetting(){
            this.ifSettingShow = true;
        },
        HideSetting(){
            this.ifSettingShow = false;
        }
    }
}
</script>

<style lang="scss">
 @import '../assets/style/global.scss';
   .menu-bar{
    .menu-wrapper{
     position: absolute;
     bottom:0;
     left:0;
     z-index: 101;
     display: flex;
     width:100%;
     height: px2rem(55);
     background: white;
     box-shadow: 0 px2rem(-8) px2rem(8) rgba(0,0,0,0.15);
     &.hide-box-shadow{
         box-shadow: none;
     }
     .icon-wrapper{
       flex:1;
       @include center;
       .icon-icon-test{
          font-size: px2rem(30);
        }
        .icon-baitianmoshimingliangmoshi{
          font-size: px2rem(30);
        }
       .icon{
         color: #333;
        font-size: px2rem(27);
       }
     }
     &.slide-up-enter, &.slide-up-leave-to{
        transform:translate3d(0,100%,0)
     }
     &.slide-up-enter-to, &.slide-up-leave{
        transform:translate3d(0,0,0)
     }
     &.slide-up-enter-active,&.slide-up-leave-active{
        transition: all .2s linear;
     }
   }
    .setting-wrapper{
           position: absolute;
           bottom: px2rem(54);
           left:0;
           width: 100%;
           height:px2rem(70);
           background: white;
           box-shadow: 0 px2rem(-8) px2rem(8) rgba(0, 0, 0, .15);
            &.slide-up-enter, &.slide-up-leave-to{
                transform:translate3d(0,px2rem(108),0)
            }
            &.slide-up-enter-to, &.slide-up-leave{
                transform:translate3d(0,0,0)
            }
            &.slide-up-enter-active,&.slide-up-leave-active{
                transition: all .2s linear;
            }
           .setting-font-size{

           }
       }
   }
   
</style>
