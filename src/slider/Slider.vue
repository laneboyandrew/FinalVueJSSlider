<template>
  <div id="slider">
    <div class="arrowLeft" @click ="arrowLeft()"> </div>
    <Slides :image="images[chosenImage]"/>
    <div class="arrowRight" @click = "arrowRight()"></div>
  </div>
</template>

<script>
  import Slides from './Slides.vue';
  export default {
    components : {
      Slides
    },
    data(){
      return{
        images : [
          {
            id: 0,
            url: "/images/image1.jpg",
            /*title: "Nassim_Taleb"*/
          },
          {
            id: 1,
            url: "/images/image2.jpg",
            /*title: "Hall"*/
          }

        ],
        chosenImage : 0,
        intervalObject : null
      }
    },
    methods :{
      arrowLeft(){
        clearInterval(this.intervalObject);
        this.moveLeft();
        var self = this;
        this.intervalObject = setInterval(()=> {
          self.moveLeft();
        },4000);
      },
      arrowRight(){
        clearInterval(this.intervalObject);
        this.moveRight();
        var self = this;
        this.intervalObject = setInterval(()=> {
          self.moveRight();
        },4000);

      },
      moveLeft(){
        var flag = this.chosenImage;
        flag--;
        if(flag < 0){
          flag = (this.images.length -1);
        }
        this.chosenImage = flag;


      },
      moveRight(){
        var flag = this.chosenImage;
        flag++;
        if (flag >= this.images.length){
          flag = 0;
        }

        this.chosenImage = flag;
      }

    },

    created(){
      var self= this;
      this.intervalObject = setInterval(()=>{
        self.moveLeft();
      },4000);
    }
  }
</script>

<style>
  #slider{
    position: relative;

  }
  #slider .arrowLeft, #slider .arrowRight {
    position: absolute;
    top: 100%;
    border: 20px solid transparent;


  }
  #slider .arrowLeft {
    border-right-color: black;
    z-index: 1;
    margin-left: 20%;
    margin-top: 17%;
  }

  #slider .arrowRight {
    right: 0;
    border-left-color: black;
    margin-right: 18%;
    margin-top: 17%;
  }


</style>
