<script>
import { ref } from 'vue';
import shop from './Shop.vue';
import why from './Why.vue';
import contact from './Contact.vue';





export default {
  name: 'HomePage',
  emits: ['response'], 
  components: {
    shop,
    why,
    contact
  },
  setup(props, { emit }) {
    const slider = ref([
    {
        id: 1,
        img: 'https://assets.goal.com/v3/assets/bltcc7a7ffd2fbf71f5/bltc4c7b260d9ef06cc/62e8b14bd130cf110c72e27e/Lusail_Stadium_(3).jpg?auto=webp&format=pjpg&width=3840&quality=60',
        title: 'Welcome To Our Sport Ticket Shop',
        description: 'we\'re more than just a ticket platform; we\'re your gateway to the heart-pounding action of your favorite sports. Explore a world of seamless ticketing, exclusive deals, and premium experiences.'
    },
    {
        id: 2,
        img: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQlr7467mOOn6iGB1yfrq4gqPmeQuFJHUpt1g&usqp=CAU',
        title: 'Elevate Your Game Day Experience! ',
        description: "Fuel your passion for sports with our provided Ticket . 🎟️ Score the hottest tickets, witness epic showdowns, and create memories that last a lifetime. From courtside excitement to stadium roars, we've got your ticket to unforgettable moments. Don't miss out – secure your seats now and immerse yourself in the thrill of victory!"
    },
    {
        id: 3,
        img: 'https://dot.la/media-library/sofi-stadiums-70000-square-foot-circular-video-board-is-dubbed-the-infinity-screen.jpg?id=29248462&width=2000&height=1500&quality=85&coordinates=0%2C0%2C0%2C0',
        title: 'Elevate Your Game Day Experience!',
        description: "Score the best seats and unforgettable moments! 🏀🏈⚽, your gateway to thrilling sports experiences. Grab your tickets now and be part of the action!"
    }

])
    const currentSlide = ref(0)

    function nextSlide() {
      currentSlide.value = (currentSlide.value + 1) % slider.value.length
    }

    function prevSlide() {
      currentSlide.value = (currentSlide.value - 1 + slider.value.length) % slider.value.length
    }  
    
    const changePage = (pageName) => {
            emit('response', pageName); // Use emit to emit the changePage event
        }

    return {
      slider,
      currentSlide,
      nextSlide,
      prevSlide,
      changePage
    }


  }
}
</script>


<template>
  <div class='slider_section'>
    <div class='carousel-item-style'>
      <div>
        <div class="row">
          <div class="col-md-1">
            <a href="#" @click="prevSlide()" class="bi bi-arrow-left-circle"></a>
          </div>
          <div class="col-md-6">
            <div class="detail-box">
              <h1>
                {{slider[currentSlide].title}}
              </h1>
              <p>
                {{slider[currentSlide].description}}
              </p>
              <a href='#' @click="changePage('contact')">
                Contact Us
              </a >
            </div>
          </div>
          <div class="col-md-4 ">
            <div class="img-box">
              <img  :src="slider[currentSlide].img" alt="" />
            </div>
          </div>
          <div class="col-md-1">
            <a href="#" @click="nextSlide()" class="bi bi-arrow-right-circle"></a>
          </div>
        </div>
      </div>
    </div>
    <div class="slider-dots">
      <span class="dot" v-for="(dot, index) in slider" :key="dot.id" :class="{ active: index === currentSlide}"></span>                
    </div>      
  </div>
  <shop />
  <why />
  <contact />
</template>

<style scoped>


.slider_section {
  position: relative;
  padding-top: 45px;
  
  padding-left: 45px;
  padding-right: 45px;  
}

.slider_section .row {
  -webkit-box-align: center;
      -ms-flex-align: center;
          align-items: center;
    padding-top: 55px;
}

.slider_section .img-box {
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-pack: center;
      -ms-flex-pack: center;
          justify-content: center;
  padding: 45px;
}

.slider_section .img-box img {
  width: 500px;
  height: 500px;
  border-radius: 90px;
  border: 15px solid #566d5f;

}

.slider_section .detail-box {
  padding-left: 45px;
  margin: 45px 0;
  max-width: 90%;
  font-size: 20px;
}

.slider_section .detail-box h1 {
  font-weight: bold;
  font-size: 3.5rem;
  margin-bottom: 10px;
}

.slider_section .detail-box a {
  display: inline-block;
  padding: 10px 40px;
  background-color: #e3d4d6;
  color: #ffffff;
  border: 1px solid #db4566;
  border-radius: 5px;
  -webkit-transition: all .3s;
  transition: all .3s;
  margin-top: 25px;
  text-transform: uppercase;
}

.slider_section .detail-box a:hover {
  background-color: transparent;
  color: #db4566;
}
.carousel-item-style {
  max-height: fit-content;
  border-radius: 30px;
  background-color: rgb(180, 237, 209);
  border-radius: 0 0 15px 15px; 

  
}

.slider-dots {
   text-align: center;
}
.slider-dots .dot {
    display: inline-block;
    width: 10px;
    height: 10px;
    border-radius: 50%;
    background-color: #f3f0f0;
    margin: 0 5px;
}

.slider-dots .dot.active {
  background-color: black;
}

.slider_section .row a {
  font-size: 30px;
  color: #db4566;
  text-decoration: none;
  font-weight: bold;
  -webkit-transition: all .3s;
  transition: all .3s;
}
</style>