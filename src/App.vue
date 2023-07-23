<script setup>
import {ref,reactive} from 'vue'
const active = ref(0)

const images=reactive([
{
      src: 'https://images.unsplash.com/photo-1470770841072-f978cf4d019e?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1470&q=80',
      title: 'Slide 1',
      heading: 'Heading text 1',
      caption: 'Lorem ipsum dolor sit amet 1'
    },
    {
      src: 'https://images.unsplash.com/photo-1532274402911-5a369e4c4bb5?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1170&q=80',
      title: 'Slide 2',
      heading: 'Heading text 2',
      caption: 'Lorem ipsum dolor sit amet 2'
    },
    {
      src: 'https://images.unsplash.com/photo-1682687980918-3c2149a8f110?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDl8fHxlbnwwfHx8fHw%3D&auto=format&fit=crop&w=500&q=60',
      title: 'Slide 3',
      heading: 'Heading text 3',
      caption: 'Lorem ipsum dolor sit amet 3'
    }
    
])


</script>

<template>
<div id="carousel-example" class="carousel " >

<ol class="carousel-indicators">
  <li @click="active = index" :class="index == active?'active':''" v-for="(image,index) in images" :key="index"></li>
  
</ol>

<div class="carousel-inner">

  <div :class="index == active?'active':''" class="item" v-for="(image ,index) in images" :key="index">
    <img :src="image.src" width="1200" height="200"/>
    <div class="carousel-caption">
        <h2>{{ image.title }}</h2>

        <h3>{{ image.heading }}</h3>
                <p>{{ image.caption }}</p>
    </div>
  </div>

  

</div>  

<!--  Controls  -->
<a class="left carousel-control"  @click.prevent="0 == active ? active = (images.length) - 1 : active--">
  <span class="glyphicon glyphicon-chevron-left"></span>
</a>
<a class="right carousel-control" @click.prevent="(images.length) - 1 == active ? active = 0 : active++">
  <span class="glyphicon glyphicon-chevron-right"></span>
</a>      


</div>
  
</template>

<style scoped>
img{
    height:500px !important;
}

#carousel-example {
  width: 1200px;
}

.carousel .carousel-caption {
  background: #222;
  opacity: 0.75;
  border-radius: 5px;
}

.carousel .carousel-caption p {
  opacity: 1 !important; 
  z-index: 20;
}

a.carousel-control:hover {
  cursor: pointer;
}

</style>
