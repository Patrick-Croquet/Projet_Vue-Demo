<template>
    <div id="carouselExampleCaptions" class="carousel slide" data-bs-ride="carousel">
        <div class="carousel-indicators">
            <button type="button" data-bs-target="#carouselExampleCaptions" data-bs-slide-to="0" class="active" aria-current="true" aria-label="Slide 1"></button>
            <button type="button" data-bs-target="#carouselExampleCaptions" data-bs-slide-to="1" aria-label="Slide 2"></button>
            <button type="button" data-bs-target="#carouselExampleCaptions" data-bs-slide-to="2" aria-label="Slide 3"></button>
        </div>
        <div class="carousel-inner">
            <!-- <div class="carousel-item active">
            <img src="@/assets/montagne1.jpg" class="d-block w-100" alt="...">
            <div class="carousel-caption d-none d-md-block">
                <h5>First slide label</h5>
                <p>Some representative placeholder content for the first slide.</p>
            </div>
            </div>
            <div class="carousel-item">
            <img src="@/assets/montagne2.jpg" class="d-block w-100" alt="...">
            <div class="carousel-caption d-none d-md-block">
                <h5>Second slide label</h5>
                <p>Some representative placeholder content for the second slide.</p>
            </div>
            </div> -->

            <Slide v-for="(slide,index) in slides" :key="index" :id="slide.id" :titre="slide.titre" :image="slide.image"  />
            
            <!-- <div class="carousel-item">
            <img src="@/assets/montagne4.jpg" class="d-block w-100" alt="...">
            <div class="carousel-caption d-none d-md-block">
                <h5>Third slide label</h5>
                <p>Some representative placeholder content for the third slide.</p>
            </div>
            </div> -->
        </div>
        <button class="carousel-control-prev" type="button" data-bs-target="#carouselExampleCaptions" data-bs-slide="prev">
            <span class="carousel-control-prev-icon" aria-hidden="true"></span>
            <span class="visually-hidden">Previous</span>
        </button>
        <button class="carousel-control-next" type="button" data-bs-target="#carouselExampleCaptions" data-bs-slide="next">
            <span class="carousel-control-next-icon" aria-hidden="true"></span>
            <span class="visually-hidden">Next</span>
        </button>
    </div>
</template>

<script>
import Slide from '@/components/Slide.vue'
import axios from 'axios'

export default {
    name: 'Carousel',
    components: {
    Slide,
    },
    props: {

    },
    /*data(){
        return {
            slides:[
                {
                    id:1,
                    titre:'First slide label',
                    image:'montagne1.jpg',
                },
                {
                    id:2,
                    titre:'Second slide label',
                    image:'montagne2.jpg',
                },
                {
                    id:3,
                    titre:'Third slide label',
                    image:'montagne4.jpg',
                },
            ],
        }
    },*/
    data(){
        return {
            slides:[],
            errors: []
        }
  },
  // Fetches Details when the component is created.
  created() {
    axios.get(`http://localhost:5173/slides.json`)
    .then(response => {
      // JSON responses are automatically parsed.
      // this.details = response.data['hydra:member'] // fonctionne avec l'api
      this.slides = response.data.slides
    })
    .catch(e => {
      this.errors.push(e)
    })
  }  
}
</script>

<style scoped>
    /* CUSTOMIZE THE CAROUSEL
    -------------------------------------------------- */
    
    /* Carousel base class */
    .carousel {
        margin-bottom: 4rem;
    }
    /* Since positioning the image, we need to help out the caption */
    .carousel-caption {
        bottom: 3rem;
        z-index: 10;
    }
</style>