<template>
  <div class="main-swiper">
    <div class="container">
      <swiper @swiper="onSwiper"
              :slidesPerView="3"
              :mousewheel="true"
              :centeredSlides="true"
              :initialSlide="initialSlide"
              :pagination="{
      clickable: true,
    }"
              :modules="modules"
      >
        <swiper-slide id="slide.id"
                      @click="handleSlideTo(slide.id)"
                      v-for="slide in slides"
        >
          <div class="slide-content">
            <div class="place">{{ slide.place }}</div>
            <div class="slide-content-text">{{ slide.text }}</div>
            <div class="time">{{ slide.time }}</div>
            <button class="ticket">Купить билеты</button>
            <div class="slide-content-hex"></div>
          </div>
        </swiper-slide>
      </swiper>
    </div>
  </div>
</template>
<script>
// Import Swiper Vue.js components
import {Swiper, SwiperSlide} from "swiper/vue";

// Import Swiper styles
import "swiper/css";

import "swiper/css/pagination";
// import required modules
import {Mousewheel} from "swiper";

export default {
  components: {
    Swiper,
    SwiperSlide,
  },
  data() {
    return {
      initialSlide: 2,

      slides: [
        {id: 1, text: '30 мая', place: 'Место 1', time: '17:00'},
        {id: 2, text: '17 июня', place: 'Место 2', time: '18:00'},
        {id: 3, text: '26 июня', place: 'Стадион', time: '19:00'},
        {id: 4, text: '16 июля', place: 'Место 3', time: '20:00'},
        {id: 5, text: '30 сентяября', place: 'Место 4', time: '21:00'},
      ],
      APIData: [],
      swiperOptions: {
        breakpoints: {
          320: {
            slidesPerView: 1,
            spaceBetween: 10
          },
          770: {
            slidesPerView: 2,
            spaceBetween: 50
          },

          771: {
            slidesPerView: 4,
            spaceBetween: 30
          }
        }
      }

    }
  },

  methods: {
    onSwiper(swiper) {
      this.swiper = swiper;
    },

    handleSlideTo(id) {
      this.swiper.slideTo(id - 1);
    },
  },

  setup() {
    return {
      modules: [Mousewheel],
    };
  },
};
</script>

<style>
.main-swiper {
  flex: 1 1 0;
}

.main-swiper .container {
  height: 100%;
}

.swiper {
  height: 100%;
}

.slide-content-text {
  width: min-content;
}

.swiper-slide-active .slide-content-text {
  width: max-content;
  font-size: 20px;
  margin: 15px 0 10px;
  font-weight: 600;
}

.place, .time, .ticket {
  display: none;
}

.swiper-slide-active .place, .swiper-slide-active .time, .swiper-slide-active .ticket {
  display: block;
}

.swiper-slide {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;

}


.ticket {
  background: none;
  margin-top: 10px;
  padding: 5px 10px;
  border-radius: 5px;
  white-space: nowrap;
  transition: all 0.3s ease;
  cursor: pointer;
}

.ticket:hover {
  background: black;
  color: white;
}


.swiper-slide-active .slide-content {
  width: 7em;
  height: 11.82em;
}



.swiper-slide-prev .slide-content,
.swiper-slide-next .slide-content {
  width: 5em;
  height: 8.32em;
}

.slide-content {
  position: relative;
  top: 0;
  margin: 0 auto;
  width: 4em;
  height: 6.52em;
  border-radius: 1em/.5em;
  background: white;
  transition: all 0.3s ease;
  color: black;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  text-align: center;
}


.slide-content:before, .slide-content:after {
  position: absolute;
  width: inherit;
  height: inherit;
  border-radius: inherit;
  background: inherit;
  content: '';
  z-index: -1;
}

.slide-content::before {
  position: absolute;
  top: 0;
  -webkit-transform: rotate(60deg);
  -ms-transform: rotate(60deg); /*Added for IE9*/
  transform: rotate(60deg)

}

.slide-content::after {
  position: absolute;
  top: 0;
  -webkit-transform: rotate(-60deg);
  -ms-transform: rotate(-60deg); /*Added for IE9*/
  transform: rotate(-60deg);
}

</style>