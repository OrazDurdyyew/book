<template>
  <div class="about">
    <div class="__container">
      <h1 class="about__title">About our website</h1>
      <p class="about__description">
        Lorem ipsum dolor sit amet consectetur adipiscing elit interdum
        ullamcorper sed pharetra sene.
      </p>
      <div class="about__images">
        <div class="about__images-image">
          <img src="@/assets/img/banner.jpg" alt="" />
        </div>
        <div class="about__images-image">
          <img src="@/assets/img/banner_2.jpg" alt="" />
        </div>
      </div>
      <div class="about__whatwedo">
        <h3 class="about__whatwedo-title">What we do</h3>
        <p class="about__whatwedo-description">
          It is a long established fact that a reader will be distracted by the
          readable content of a page when looking at its layout. The point of
          using Lorem Ipsum is that it has a more-or-less normal distribution of
          letters, as opposed to using. Content here', making it look like
          readable English. Many desktop publishing packages and web page
          editors now use Lorem Ipsum as their default model text, and a search
          for 'lorem ipsum' will uncover many web sites still in their infancy.
        </p>
      </div>
      <div class="about__counters">
        <div
          class="about__counters-item"
          v-for="item in items"
          :key="item.uuid"
        >
          <div class="about__counters-flex">
            <span>{{ item.counter }}</span>
            <base-icon :icon="item.icon" />
          </div>
          <p>{{ item.title }}</p>
        </div>
      </div>
      <div class="about__mission">
        <div class="about__mission-content">
          <h2>Our Mission</h2>
          <p>
            Lorem ipsum dolor sit amet, consectetur adipiscing Ld eu aliquet
            diam lorem viverra at justo. Nulla odio nequefjf gravida in pharetra
            egestas. Ac id sagittis at morbi interdum nibh diam sagittis et.
            Lorem ipsum dolor sit amet, consectetur adipiscing Pharetra id eu
            aliquet diam lorem viverra at justo. Nulla odio nequesg gravida in
            pharetra egestas.
          </p>
        </div>
        <div class="about__mission-image">
          <img src="@/assets/img/banner.jpg" alt="" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      items: [
        {
          counter: '10',
          icon: 'allBook',
          title: 'All books',
        },
        {
          counter: '30',
          icon: 'download',
          title: 'Download',
        },
        {
          counter: '40',
          icon: 'book',
          title: 'Books',
        },
        {
          counter: '50',
          icon: 'audioBook',
          title: 'Audio books',
        },
      ],
    }
  },
}
</script>

<style lang="scss" scoped>
.about {
  margin-top: 70px;
  @media (max-width: 767px) {
    margin-top: 30px;
  }
  &__title {
    color: #333;
    font-size: 75px;
    font-weight: 800;
    line-height: 110%;
    text-align: center;
    margin-bottom: 6px;
    @media (max-width: 767px) {
      font-size: 34px;
    }
  }

  &__description {
    text-align: center;
    color: var(--gray);
    font-size: 25px;
    font-weight: 400;
    line-height: 150%;
    max-width: 646px;
    margin: 0 auto;
    margin-bottom: 50px;
    @media (max-width: 767px) {
      font-size: 16px;
      max-width: 400px;
      margin-bottom: 20px;
    }
  }

  &__images {
    display: grid;
    grid-template-columns: 1fr 476px;
    gap: 30px;
    height: 583px;
    margin-bottom: 50px;
    transition: all 0.3s ease 0s;
    @media (max-width: 767px) {
      margin-bottom: 30px;
      grid-template-columns: 1fr;
      gap: 15px;
      height: 350px;
    }
    @media (max-width: 479px) {
      margin-bottom: 30px;
      grid-template-columns: 1fr;
      gap: 15px;
      height: 250px;
    }
  }

  &__images-image {
    width: 100%;
    height: 100%;
    transition: all 0.3s ease 0s;
    @media (max-width: 479px) {
      height: 250px;
    }
    &:last-child {
      @media (max-width: 767px) {
        display: none;
      }
    }
    img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      object-position: center;
      border-radius: 20px;
    }
  }

  &__whatwedo {
    display: grid;
    grid-template-columns: 500px 1fr;
    margin-bottom: 50px;
    @media (max-width: 767px) {
      margin-bottom: 30px;
      grid-template-columns: 1fr;
    }
  }

  &__whatwedo-title {
    color: var(--text);
    font-size: 50px;
    font-weight: 800;
    line-height: 110%;
    @media (max-width: 767px) {
      font-size: 26px;
      margin-bottom: 6px;
    }
  }

  &__whatwedo-description {
    color: var(--gray);
    font-size: 22px;
    font-weight: 400;
    line-height: 157.4%;
    @media (max-width: 767px) {
      font-size: 16px;
      line-height: 130%;
      text-align: justify;
    }
  }

  &__counters {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 130px;
    padding: 60px 70px;
    background-color: var(--grayLight);
    border-radius: 50px;
    margin-bottom: 100px;
    @media (max-width: 1100px) {
      gap: 80px;
    }
    @media (max-width: 992px) {
      gap: 50px;
      grid-template-columns: repeat(2, 1fr);
    }
    @media (max-width: 767px) {
      margin-bottom: 30px;
      padding: 30px 40px;
    }
    @media (max-width: 479px) {
      grid-template-columns: repeat(2, 1fr);
      gap: 30px;
      padding: 20px 30px;
    }
  }

  &__counters-item {
    p {
      color: var(--text);
      text-align: center;
      font-size: 25px;
      font-weight: 700;
      line-height: 157.4%;
      margin-top: 10px;
      @media (max-width: 767px) {
        font-size: 18px;
        margin-top: 0;
      }
    }
  }

  &__counters-flex {
    display: flex;
    justify-content: space-around;
    @media (max-width: 992px) {
      justify-content: center;
    }
    @media (max-width: 767px) {
      gap: 6px;
    }
    span {
      &:first-child {
        color: var(--text);
        font-size: 75px;
        font-weight: 800;
        line-height: 110%;
        @media (max-width: 767px) {
          font-size: 40px;
        }
      }
      &:last-child {
        &:deep(svg) {
          width: 61px;
          height: 51px;
          color: var(--primary);
          flex: 1 1 auto;
          @media (max-width: 767px) {
            width: 41px;
            height: 31px;
          }
        }
      }
    }
  }

  &__mission {
    display: grid;
    grid-template-columns: minmax(30%, 43%) 1fr;
    gap: 12px;
    @media (max-width: 767px) {
      grid-template-columns: 1fr;
    }
  }

  &__mission-content {
    h2 {
      color: var(--text2);
      font-size: 50px;
      font-weight: 800;
      line-height: 110%;
      margin-bottom: 24px;
      @media (max-width: 767px) {
        font-size: 26px;
        margin-bottom: 6px;
      }
    }
    p {
      color: var(--gray);
      font-size: 22px;
      font-weight: 400;
      line-height: 157.4%;
      @media (max-width: 767px) {
        font-size: 16px;
        left: 130%;
      }
    }
  }

  &__mission-image {
    border-radius: 50px;
    height: 400px;
    img {
      width: 100%;
      height: 100%;
      border-radius: 50px;
      object-fit: cover;
      object-position: center;
    }
    @media (max-width: 479px) {
      height: 300px;
      border-radius: 10px;
    }
  }
}
</style>
