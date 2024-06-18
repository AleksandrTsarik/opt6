<template>
  <div class="document">
    <h2 class="document__title title">Документы</h2>
    <div class="document__slider">
      <swiper
        :grabCursor="true"
        :spaceBetween="38"
        :navigation="true"
        :loop="true"
        :pagination="{
          clickable: true,
          dynamicBullets: true,
        }"
        :modules="modules"
        :breakpoints="{
          1024: {
            slidesPerView: 3,
            slidesPerGroup: 3
          },
          768: {
            slidesPerView: 2,
            slidesPerGroup: 2
          },
          575: {
            slidesPerView: 1,
            slidesPerGroup: 1
          }
        }"
        class="document-slider"
      >
        <swiper-slide
          v-for="(slide, i) in slider"
          :key="i"
        >
          <div class="document-slider__item">
            <div class="document-slider__info">
              <div class="document-slider__title">{{ slide.title }}</div>
              <div class="document-slider__text">{{ slide.text }}</div>
            </div>
            <div class="document-slider__link">
              <NuxtLink :to="slide.url"  class="btn btn-dark">Перейти</NuxtLink>
            </div>
          </div>
        </swiper-slide>
      </swiper>
    </div>
  </div>
</template>

<script>
import {Swiper, SwiperSlide} from 'swiper/vue';
import 'swiper/css';

import 'swiper/css/free-mode';
import 'swiper/css/navigation';
import 'swiper/css/pagination';
import { Navigation, Mousewheel, Pagination } from 'swiper/modules';
export default {
  components: {
    Swiper,
    SwiperSlide,
  },
  data() {
    return {
      slider: [
        {
          title: 'Лицензионный договор',
          text: 'Механизм разбрасывания веерного типа приводится в действие от колес тележки, отличается простой и надежной конструкцией, не нуждается в смазке.',
          url: '/license'
        },
        {
          title: 'Политика обработки персональных данных',
          text: 'Радиус разброса ПГМ составляет до 3 метров и может регулироваться.',
          url: '/license'
        },
        {
          title: 'Информация об оплате',
          text: 'Десятипозиционный переключатель дозировки расположен на ручке тележки и позволяет очень точно регулировать объем рассыпаемого реагента с учетом его массы и фракции.',
          url: '/license'
        },
        {
          title: 'Лицензионный договор',
          text: 'Механизм разбрасывания веерного типа приводится в действие от колес тележки, отличается простой и надежной конструкцией, не нуждается в смазке.',
          url: '/license'
        },
        {
          title: 'Политика обработки персональных данных',
          text: 'Радиус разброса ПГМ составляет до 3 метров и может регулироваться.',
          url: '/license'
        },
        {
          title: 'Информация об оплате',
          text: 'Десятипозиционный переключатель дозировки расположен на ручке тележки и позволяет очень точно регулировать объем рассыпаемого реагента с учетом его массы и фракции.',
          url: '/license'
        },
      ]
    }
  },
  setup() {
    return {
      modules: [ Navigation,  Mousewheel, Pagination],
    };
  }
}
</script>

<style lang="scss">
  .document {
    &__title {
      text-align: center;
      margin-bottom: 40px;
    }
  }
  .document-slider {
    display: flex;
    height: 100%;
    align-items: stretch;
    padding: 25px 20px;
    overflow: hidden;
    .swiper-slide {
      height: 450px;
    }
    .swiper-button-prev, .swiper-button-next {
      display: block;
      width: 40px;
      height: 80px;
      background-color: rgba(#D5DDEA, 0.8);
      top: 50%;
      transform: translateY(-50%);
      &:after {
        content: '';
        background-image: url('@/assets/img/arrow.svg');
        width: 14px;
        height: 27px;
        display: block;
        background-repeat: no-repeat;
        background-size: cover;
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
      }
    }
    .swiper-button-prev  {
      border-radius: 0 50px 50px 0;
      
    }
    .swiper-button-next {
      border-radius: 50px 0 0 50px;
      &:after {
        transform:  translate(-50%, -50%) rotate(180deg);
      }
    }
    &__item {
      background-color: #fff;
      border: solid 1px #EEEFF1;
      box-shadow: 0px 0px 20px rgba(0, 0, 0, 0.12);
      border-radius: 10px;
      padding: 25px;
      height: 100%;
      display: flex;
      flex-direction: column;
    }
    &__title {
      font-size: 31px;
      color: #1253A2;
      font-weight: 700;
      margin-bottom: 15px;
    }
    &__text {
      font-size: 18px;
    }
    &__link {
      margin-top: auto;
      a {
        display: block;
        text-align: center;
      }
    }
  }
</style>