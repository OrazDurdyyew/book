<template>
  <div class="swiper-block">
    <div v-swiper:mySwiper="options" class="swiper-block__swiper swiper">
      <div class="swiper-block__wrapper swiper-wrapper">
        <div class="swiper-block__slide swiper-slide">
          <div class="swiper-block__image">
            <img src="@/assets/img/banner.jpg" alt="" />
          </div>
          <div div class="swiper-block__title">
            <h1>There is nothing better than to read</h1>
          </div>
        </div>
        <div class="swiper-block__slide swiper-slide">
          <div class="swiper-block__image">
            <img src="@/assets/img/banner_2.jpg" alt="" />
          </div>
          <div class="swiper-block__title">
            <h1>There is nothing better than to read</h1>
          </div>
        </div>
      </div>
      <div class="swiper-block__bullets-wrapper">
        <div class="swiper-block__bullets swiper-pagination-bullet"></div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      sliderImages: [],
      options: {
        loop: true,
        slidesPerView: 1,
        speed: 1200,
        spaceBetween: 10,
        autoplay: {
          delay: 5000,
        },
        pagination: {
          el: '.swiper-pagination-bullet',
          clickable: true,
        },
      },
    }
  },
}
</script>

<style lang="scss" scoped>
.swiper-block {
  height: calc(100vh - 320px);
  margin-bottom: 40px;
  @media (max-width: 767px) {
    margin-bottom: 30px;
    height: calc(100vh - 500px);
  }
	@media (max-width: 479px) {
    height: calc(100vh - 600px);
  }
  // .swiper-block__swiper

  &__swiper {
    height: 100%;
    position: relative;
  }

  // .swiper-block__wrapper

  &__wrapper {
    display: flex;
    width: fit-content;
    height: 100%;
    position: relative;
    &::before {
      content: '';
      position: absolute;
      width: 100%;
      height: 100%;
      background-color: rgba(0, 0, 0, 0.3);
      z-index: 10;
    }
  }

  // .swiper-block__slide

  &__slide {
    height: 100%;
    position: relative;
  }

  // .swiper-block__image

  &__image {
    height: 100%;
    img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      object-position: center;
    }
  }

  // .swiper-block__title

  &__title {
    position: absolute;
    z-index: 10;
    left: 0;
    top: 50%;
    transform: translateY(-50%);
    width: 100%;
    font-family: 'Bloverly' !important;
    h1 {
      max-width: 1000px;
      margin: 0 auto;
      color: #fff;
      text-align: center;
      font-size: 100px;
      font-weight: 400;
    }
    @media (max-width: 767px) {
      h1 {
        max-width: calc(100% - 30%);
        font-size: 44px;
      }
    }
    @media (max-width: 479px) {
      h1 {
        max-width: calc(100% - 20%);
        font-size: 30px;
      }
    }
  }

  // .swiper-block__bullets-wrapper

  &__bullets-wrapper {
    position: absolute;
    bottom: 20px;
    left: 50%;
    transform: translateX(-50%);
    width: 30%;
    z-index: 10;
  }

  // .swiper-block__bullets

  &__bullets {
    display: flex;
    justify-content: center;
    gap: 10px;
    &:deep {
      .swiper-pagination-bullet {
        cursor: pointer;
        width: 10px;
        height: 10px;
        border-radius: 50%;
        border: 1px solid #fff;
        background-color: transparent;
      }
      .swiper-pagination-bullet-active {
        background-color: #fff;
      }
    }
  }
}

.relative {
  position: relative;
}
</style>
