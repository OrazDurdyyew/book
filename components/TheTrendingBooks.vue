<template>
  <div :class="['trending-books', { background: background }]">
    <div class="trending-books__container">
      <the-title-main title="Trending Now" icon="headPhone"></the-title-main>
      <div class="trending-books-swiper">
        <div class="trending-books-swiper__container">
          <div
            v-swiper:mySwiper="options"
            :class="[
              'trending-books-swiper__swiper swiper',
              { background: background },
            ]"
          >
            <div class="trending-books-swiper__wrapper swiper-wrapper">
              <div
                class="trending-books-swiper__slide swiper-slide"
                v-for="item in 10"
                :key="item.uuid"
                @click="$router.push(localeLocation(`/books/${item.uuid}`))"
              >
                <div class="trending-books-swiper__image">
                  <img src="@/assets/img/book_2.png" alt="" />
                </div>
                <h3 class="trending-books-swiper__title">JENNY LAWSON</h3>
                <h4 class="trending-books-swiper__sub-title">JENNY LAWSON</h4>
                <div class="flex flex-y-center gap-4">
                  <base-icon icon="redLike" />
                  <p class="trending-books-swiper__like-number">125</p>
                </div>
              </div>
            </div>
            <div class="trending-books-swiper__navigations">
              <div class="trending-books-swiper__navigation-wrapper">
                <div
                  class="trending-books-swiper__navigation swiper-button-prev"
                  slot="button-prev"
                >
                  <base-icon icon="navigationLeft" />
                </div>
              </div>
              <div class="trending-books-swiper__navigation-wrapper">
                <div
                  class="trending-books-swiper__navigation swiper-button-next"
                  slot="button-next"
                >
                  <base-icon icon="navigationRight" />
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    background: {
      type: Boolean,
      default: () => null,
    },
  },
  data() {
    return {
      options: {
        loop: true,
        slidesPerView: 7,
        spaceBetween: 30,
        speed: 400,
        slidesPerView: 1,
        navigation: {
          nextEl: '.swiper-button-next',
          prevEl: '.swiper-button-prev',
        },
        breakpoints: {
          370: {
            slidesPerView: 2,
          },
          479: {
            slidesPerView: 4,
          },
          767: {
            slidesPerView: 5,
            spaceBetween: 40,
          },
          992: {
            slidesPerView: 5,
            spaceBetween: 60,
          },
        },
      },
    }
  },
}
</script>

<style lang="scss" scoped>
.trending-books {
  padding: 60px 0;
  background-color: #f7f5ff;
  &.background {
    background-color: transparent !important;
  }
  @media (max-width: 767px) {
    padding: 30px 0;
  }
}
.trending-books-swiper {
  margin-bottom: 40px;
  @media (max-width: 767px) {
    margin-bottom: 30px;
  }
  // .trending-books-swiper__swiper

  &__swiper {
    max-width: 1440px;
    margin: 0 auto;
    padding: 0 20px;
    position: relative;
    &.background {
      &::before {
        content: '';
        background-color: #fff;
      }
      &::after {
        content: '';
        background-color: #fff;
      }
    }
    &::before {
      content: '';
      background-color: #f7f5ff;
      height: 120%;
      position: absolute;
      top: -10px;
      transform: translate(-101%);
      width: 100vw;
      z-index: 3;
    }
    &::after {
      content: '';
      background-color: #f7f5ff;
      height: 120%;
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

  // .trending-books-swiper__wrapper

  &__wrapper {
    display: grid;
    grid-template-columns: repeat(5, 1fr);
    grid-auto-flow: column;
  }

  // .trending-books-swiper__slide

  &__slide {
    cursor: pointer;
    height: 100%;
  }

  // .trending-books-swiper__image

  &__image {
    width: 100%;
    position: relative;
    display: flex;
    align-items: flex-start;
    justify-content: center;
    cursor: pointer;
    box-shadow: 0.1px 0.1px 3px;
    border-radius: 10px;
    img {
      width: 100%;
      height: 100%;
      border-radius: 10px;
    }
  }

  // .trending-books-swiper__title

  &__title {
    color: var(--primary);
    font-size: 12px;
    font-weight: 800;
    letter-spacing: 1px;
    margin: 8px 0;
    @media (max-width: 767px) {
      font-size: 10px;
    }
    @media (max-width: 479px) {
      font-size: 8px;
      margin-bottom: 4px;
    }
  }

  &__sub-title {
    color: var(--text);
    font-size: 16px;
    font-weight: 800;
    margin-bottom: 8px;
    @media (max-width: 767px) {
      font-size: 14px;
    }
    @media (max-width: 479px) {
      font-size: 12px;
      margin-bottom: 4px;
    }
  }

  &__like-number {
    color: var(--text);
    font-size: 12px;
    font-weight: 800;
    @media (max-width: 479px) {
      font-size: 10px;
    }
  }

  // .trending-books-swiper__navigations

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

  // .trending-books-swiper__navigation

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
