<template>
  <div class="main-swiper">
    <swiper @swiper="onSwiper"
            :slidesPerView="2"
            :mousewheel="true"
            :centeredSlides="true"
            :breakpoints="{576:{ slidesPerView:3}, 1024:{ slidesPerView:5}}"
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
        <div class="first-team">
          {{ slide.firstTeam }}
        </div>

        <div class="slide-content">

          <div class="place">{{ slide.place }}</div>
          <div class="slide-content-text">{{ slide.text }}</div>
          <div class="time">{{ slide.time }}</div>
          <button class="ticket">Купить билеты</button>
          <div class="slide-content-hex"></div>

        </div>
        <div class="second-team">
          {{ slide.secondTeam }}
        </div>
      </swiper-slide>
    </swiper>
  </div>
</template>
<script>
import {Swiper, SwiperSlide} from "swiper/vue";
import "swiper/css";
import "swiper/css/pagination";
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
        {id: 1, text: '30 мая', place: 'Место 1', time: '17:00', firstTeam: 'Соперник 5', secondTeam: 'Соперник 6'},
        {id: 2, text: '17 июня', place: 'Место 2', time: '18:00', firstTeam: 'Соперник 3', secondTeam: 'Соперник 4'},
        {id: 3, text: '26 июня', place: 'Стадион', time: '19:00', firstTeam: 'Соперник 1', secondTeam: 'Соперник 2'},
        {id: 4, text: '16 июля', place: 'Место 3', time: '20:00', firstTeam: 'Соперник 7', secondTeam: 'Соперник 8'},
        {
          id: 5,
          text: '30 сентября',
          place: 'Место 4',
          time: '21:00',
          firstTeam: 'Соперник 9',
          secondTeam: 'Соперник 10'
        },
      ],
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
  position: relative;
  min-height: 730px;
}

.main-swiper:before {
  content: '';
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 70vw;
  height: 60vw;
  border-radius: 50%;
  border: 1px white solid;
}

.main-swiper:after {
  content: '';
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 40vw;
  height: 40vw;
  border-radius: 50%;
  border: 1px white solid;
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
  color: black;
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
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  text-align: center;
  cursor: pointer;
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

.first-team, .second-team {
  opacity: 0;
  font-size: 20px;
  font-weight: 600;
  transition: left 0.3s ease;
}

.swiper-slide-active .first-team,
.swiper-slide-active .second-team {
  opacity: 1;
}

.first-team {
  margin-bottom: 60px;
  position: relative;
}

.first-team:before {
  content: '';
  position: absolute;
  top: -40px;
  right: -30px;
  width: 2000px;
  height: 100px;
  -webkit-transform: skew(-30deg);
  -moz-transform: skew(-30deg);
  -o-transform: skew(-30deg);
  background: white;
  border-radius: 15px;
  z-index: -2;
}

.second-team {
  margin-top: 60px;
  position: relative;
}

.second-team:before {
  content: '';
  position: absolute;
  top: -40px;
  left: -30px;
  width: 2000px;
  height: 100px;
  -webkit-transform: skew(-30deg);
  -moz-transform: skew(-30deg);
  -o-transform: skew(-30deg);
  background: white;
  border-radius: 15px;
  z-index: -2;
}



@media (max-width: 1024px) {
  .main-swiper:before {
    width: 100vw;
    height: 100vw;
  }

  .main-swiper:after {
    width: 40vw;
    height: 40vw;
  }
}

@media (max-width: 768px) {

  .main-swiper {
    min-height: auto;
  }

}

</style>