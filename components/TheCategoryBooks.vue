<template>
  <div class="category-books">
    <div class="category-books__container">
      <div v-swiper:mySwiper="options" class="category-books__swiper swiper">
        <div class="category-books__wrapper swiper-wrapper">
          <div
            class="category-books__slide swiper-slide"
            v-for="item in 10"
            :key="item.uuid"
          >
            <div class="category-books__image">
              <img src="@/assets/img/book.png" alt="" />
            </div>
            <h3 class="category-books__title">Ertekiler</h3>
          </div>
        </div>
        <div class="category-books__navigations">
          <div class="category-books__navigation-wrapper">
            <div
              class="category-books__navigation swiper-button-prev"
              slot="button-prev"
            >
              <base-icon icon="navigationLeft" />
            </div>
          </div>
          <div class="category-books__navigation-wrapper">
            <div
              class="category-books__navigation swiper-button-next"
              slot="button-next"
            >
              <base-icon icon="navigationRight" />
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      options: {
        loop: true,
        slidesPerView: 7,
        spaceBetween: 40,
        speed: 400,
        slidesPerView: 2,
        navigation: {
          nextEl: '.swiper-button-next',
          prevEl: '.swiper-button-prev',
        },
        breakpoints: {
          320: {
            slidesPerView: 3,
            spaceBetween: 30,
          },
          479: {
            slidesPerView: 4,
            spaceBetween: 30,
          },
          767: {
            slidesPerView: 5,
          },
          992: {
            slidesPerView: 7,
          },
        },
      },
    }
  },
}
</script>

<style lang="scss" scoped>
.category-books {
  margin-bottom: 40px;
  @media (max-width: 767px) {
    margin-bottom: 30px;
  }
  // .category-books__swiper

  &__swiper {
    max-width: 1440px;
    margin: 0 auto;
    padding: 0 20px;
    position: relative;
    &::before {
      content: '';
      background-color: #fff;
      height: 110%;
      position: absolute;
      top: -10px;
      transform: translate(-101%);
      width: 100vw;
      z-index: 3;
    }
    &::after {
      content: '';
      background-color: #fff;
      height: 110%;
      position: absolute;
      top: -10px;
      right: 0;
      transform: translate(100%);
      width: 100vw;
      z-index: 3;
      @media (max-width: 767px) {
        transform: translate(96%);
      }
    }
  }

  &__container {
    @media (max-width: 767px) {
      padding: 0;
    }
  }

  // .category-books__wrapper

  &__wrapper {
    display: grid;
    grid-template-columns: repeat(7, 1fr);
    grid-auto-flow: column;
  }

  // .category-books__slide

  &__slide {
    cursor: pointer;
    height: 100%;
  }

  // .category-books__image

  &__image {
    width: 100%;
    position: relative;
    display: flex;
    align-items: flex-start;
    justify-content: center;
    img {
      width: calc(100% - 30%);
      margin: 0 auto;
    }
    &::before {
      content: '';
      position: absolute;
      width: 100%;
      height: 100%;
      background-color: #eaeeed;
      border-radius: 45%;
      z-index: -1;
      box-shadow: 0.1px 0.1px 3px;
    }
  }

  // .category-books__title

  &__title {
    margin-top: 12px;
    font-size: 20px;
    color: var(--text);
    font-weight: 700;
    text-align: center;
    @media (max-width: 767px) {
      font-size: 16px;
    }
  }

  // .category-books__navigations

  &__navigations {
    display: flex;
    z-index: 10;
    @media (max-width: 767px) {
      display: none;
    }
  }

  &__navigation-wrapper {
    width: 53px;
    height: 53px;
    border-radius: 50%;
    top: 50%;
    transform: translateY(-50%);
    position: absolute;
    z-index: 20;
    cursor: pointer;
    &:first-child {
      left: -50px;
    }
    &:last-child {
      right: -50px;
    }
    @media (max-width: 1440px) {
      &:first-child {
        left: -25px;
      }
      &:last-child {
        right: -25px;
      }
    }
    @media (max-width: 767px) {
      width: 43px;
      height: 43px;
      &:first-child {
        left: 0;
      }
      &:last-child {
        right: 0;
      }
    }
  }

  // .category-books__navigation

  &__navigation {
    color: #33333380;
    border-radius: 50%;
    background-color: transparent;
    width: 50px;
    height: 50px;
    display: flex;
    justify-content: center;
    align-items: center;
    transition: 0.3s ease 0s;
    &:deep(svg) {
      width: 40px;
      height: 40px;
    }
    &:active {
      width: 53px;
      height: 53px;
    }
    @media (max-width: 767px) {
      width: 40px;
      height: 40px;
      &:deep(svg) {
        width: 30px;
        height: 30px;
      }
      &:active {
        width: 43px;
        height: 43px;
      }
    }
  }
}
</style>
