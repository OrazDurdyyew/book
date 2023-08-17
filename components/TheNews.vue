<template>
  <div class="news">
    <div class="news__container">
      <the-title-main title="News" icon="headPhone"></the-title-main>
      <div class="news__row">
        <div class="news__columns">
          <div class="news__column" v-for="item in 3" :key="item.uuid">
            <div class="news__column-image">
              <img src="@/assets/img/banner.jpg" alt="" />
            </div>
            <div class="news__column-content">
              <h4 class="news__column-title">Nov14, 2023</h4>
              <p class="news__column-text">
                Lorem ipsum dolor sit amet consectetur, adipisicing elit.
                Exercitationem qui est debitis expedita blanditiis eum ad
                nesciunt quisquam hic ipsum!
              </p>
            </div>
          </div>
        </div>
        <div class="news__item-wrapper">
          <div class="news__item">
            <div class="news__item-image">
              <img src="@/assets/img/banner_2.jpg" alt="" />
            </div>
            <div class="news__item-content">
              <p class="news__item-date">OCTOBER11, 2023 - bY ADMIN</p>
              <h3 class="news__item-title">
                Behind the Scenes with Author Victoria Aveyard
              </h3>
              <div class="flex flex-sb flex-y-center mt-1">
                <p class="news__item-sub-title">In Education & Reference</p>
                <p class="flex flex-y-center gap-4">
                  <span class="news__item-sub-title">Read more</span>
                  <base-icon icon="navigationRight" class="news__navigation" />
                </p>
              </div>
            </div>
          </div>
        </div>
        <div class="news__columns">
          <div class="news__column" v-for="item in 3" :key="item.uuid">
            <div class="news__column-image">
              <img src="@/assets/img/banner.jpg" alt="" />
            </div>
            <div class="news__column-content">
              <h4 class="news__column-title">Nov14, 2023</h4>
              <p class="news__column-text">
                Lorem ipsum dolor sit amet consectetur, adipisicing elit.
                Exercitationem qui est debitis expedita blanditiis eum ad
                nesciunt quisquam hic ipsum!
              </p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {}
</script>

<style lang="scss" scoped>
.news {
  padding: 60px 0 0 0;
  background-color: #fff;
  @media (max-width: 767px) {
    padding: 30px 0 0 0;
  }
  // .news__container

  &__container {
  }

  // .news__row

  &__row {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 33px;
    @media (max-width: 992px) {
      grid-template-columns: repeat(1, 1fr);
      grid-template-rows: repeat(2, 1fr);
      gap: 20px;
    }
  }

  // .news__columns

  &__columns {
    display: flex;
    flex-direction: column;
    gap: 33px;
    @media (max-width: 992px) {
      order: 2;
      &:last-child {
        display: none;
      }
    }
  }

  // .news__column

  &__column {
    display: flex;
    align-items: center;
    gap: 10px;
    cursor: pointer;
    transition: 0.1s ease 0s;
    @media (max-width: 767px) {
      gap: 8px;
    }
    &:hover {
			gap: 8px;
      .news__column-image {
        min-width: 135px;
      }
    }
  }

  // .news__column-image

  &__column-image {
    min-width: 130px;
    height: 90px;
    border-radius: 10px;
    transition: all 0.1s ease 0s;
    img {
      width: 100%;
      height: 100%;
      border-radius: 10px;
      object-fit: cover;
      object-position: center;
    }
    @media (max-width: 767px) {
      min-width: 110px;
      height: 80px;
    }
  }

  // .news__column-content

  &__column-content {
    flex: 1 1 auto;
  }

  // .news__column-title

  &__column-title {
    color: var(--primary);
    font-size: 12px;
    font-weight: 800;
    letter-spacing: 1px;
    text-transform: uppercase;
    margin-bottom: 10px;
    @media (max-width: 767px) {
      gap: 8px;
      font-size: 12px;
      margin-bottom: 6px;
    }
  }

  // .news__column-text

  &__column-text {
    color: var(--text);
    text-align: justify;
    font-weight: 500;
    font-size: 14px;
    overflow: hidden;
    text-overflow: ellipsis;
    display: -webkit-box;
    -webkit-box-orient: vertical;
    -webkit-line-clamp: 3;
    word-break: break-all;
  }

  // .news__item-wrapper

  &__item-wrapper {
    width: 100%;
    height: 100%;
  }

  // .news__item

  &__item {
    position: relative;
    width: 100%;
    height: 100%;
    transition: all 0.3s ease 0s;
    cursor: pointer;
    &::before {
      content: '';
      position: absolute;
      left: 0;
      bottom: 0;
      transform: rotate(180deg);
      width: 100%;
      height: 100%;
      border-radius: 8px;
      transition: all 0.3s ease 0s;
    }
    &:hover {
      transition: 0.3s ease 0s;
      &::before {
        content: '';
        background: linear-gradient(
          180deg,
          #5746c7 0%,
          rgba(66, 0, 106, 0) 100%
        );
      }
      .news__item-content {
        opacity: 1;
        visibility: visible;
        transform: translateY(0px);
      }
    }
    @media (max-width: 767px) {
      order: 1;
      &::before {
        content: '';
        position: absolute;
        left: 0;
        bottom: 0;
        transform: rotate(180deg);
        width: 100%;
        height: 100%;
        border-radius: 8px;
        transition: all 0.3s ease 0s;
        background: linear-gradient(
          180deg,
          #5746c7 0%,
          rgba(66, 0, 106, 0) 100%
        );
      }
    }
  }

  // .news__item-image

  &__item-image {
    width: 100%;
    height: 100%;
    img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      object-position: center;
      border-radius: 10px;
    }
  }

  // .news__item-content

  &__item-content {
    width: calc(100% - 40px);
    position: absolute;
    bottom: 20px;
    left: 20px;
    right: 20px;
    opacity: 0;
    visibility: hidden;
    transform: translateY(15px);
    transition: all 0.3s ease 0s;
    @media (max-width: 767px) {
      visibility: visible;
      opacity: 1;
      transform: translateY(0);
    }
  }

  // .news__item-date

  &__item-date {
    color: #fff;
    font-size: 12px;
    font-weight: 500;
    letter-spacing: 1px;
    text-transform: uppercase;
    margin-bottom: 4px;
  }

  // .news__item-title

  &__item-title {
    color: #fff;
    font-size: 24px;
    font-weight: 700;
    padding-bottom: 10px;
    border-bottom: 1px solid rgba(255, 255, 255, 0.5);
  }

  // .news__item-sub-title

  &__item-sub-title {
    color: #fff;
    font-size: 14px;
    font-weight: 500;
  }

  // .news__navigation

  &__navigation {
    width: 14px;
    height: 14px;
    color: #fff;
  }
}
</style>
