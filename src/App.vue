<template>
  <div id="app">
    <router-view/>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style lang="scss">
*{
  margin:0;
  padding:0;
}
//rem转换px

//1rem = fontSize px
//1px = (1/fontSize)rem
$fontSize:37.5;
@function px2rem($px){
    @return ($px/$fontSize)+rem;
}

@mixin center() {
    display: flex;
    justify-content: center;
    align-items: center;
}
</style>
