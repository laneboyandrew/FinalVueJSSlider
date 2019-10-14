<template>
  <div id="slides">
    <div class="slideImage" :style="setBackgroundImage">
      </div>
    </div>

</template>

<script>
  export default {
      props: ["image"],
      computed:{
          setBackgroundImage(){
              return {backgroundImage: "url("+this.image.url+")"};
          }
      }

  }
</script>

<style>
  #slides{

  }
  #slides .slideImage{
    height: 50vh;
    width: 50%;
    background-position:center;
    background-repeat: no-repeat;
    background-size: cover;
    /* background-image:url("/images/image1.jpg"); */
  }
  #slides .slideImage .slideTitle{
    color: ;
  }
</style>
