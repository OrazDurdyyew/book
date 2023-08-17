<template>
  <div class="contact">
    <div class="contact__container">
      <h1 class="contact__title">Get in touch today!</h1>
      <div class="contact__items">
        <div class="contact__item">
          <div class="contact__item-flex">
            <base-icon icon="messageContact" class="cn" />
            <span>Mail Us</span>
          </div>
          <span>Kitaphanam.com@gmail.com</span>
        </div>
        <div class="contact__item">
          <div class="contact__item-flex">
            <base-icon icon="callContact" class="cn" />
            <span>Call Us</span>
          </div>
          <span>+(933 65) XX XX XX</span>
        </div>
      </div>
      <div class="contact__form-block">
        <form class="contact__form" @submit.prevent>
          <div class="contact__form-row">
            <base-input label="Full Name*" placeholder="..."> </base-input>
            <base-input label="Full Name*" placeholder="..."> </base-input>
            <base-input label="Full Name*" placeholder="..."> </base-input>
            <base-input label="Full Name*" placeholder="..."> </base-input>
          </div>
          <base-textarea
            label="Full Name*"
            placeholder="..."
            height="300"
            class="contact__form-textarea"
          >
          </base-textarea>
          <div class="flex flex-x-center">
            <base-button contact hoverEffect widthFull> Send Message </base-button>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
export default {}
</script>

<style lang="scss" scoped>
.cn {
  cursor: auto;
}
.contact {
  margin-top: 70px;
  @media (max-width: 767px) {
    margin-top: 30px;
  }
  &__container {
  }

  &__title {
    color: #333;
    font-size: 75px;
    font-weight: 800;
    line-height: 110%;
    text-align: center;
    margin-bottom: 30px;
    @media (max-width: 767px) {
      font-size: 34px;
      margin-bottom: 20px;
    }
  }

  &__items {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 26px;
    margin-bottom: 50px;
    @media (max-width: 992px) {
      gap: 16px;
      grid-template-columns: 1fr;
    }
  }

  &__item {
    padding: 34px 36px;
    box-shadow: 0px 24px 33px 0px rgba(181, 181, 181, 0.25);
    border-radius: 40px;
    border: 1px solid #e8e8e8;
    display: flex;
    align-items: center;
    justify-content: space-between;
    span {
      color: var(--gray);
      font-size: 22px;
      font-weight: 400;
      line-height: 157.4%;
    }
    @media (max-width: 767px) {
      padding: 26px 28px;
      span {
        font-size: 18px;
        line-height: 130%;
      }
    }
    @media (max-width: 479px) {
      padding: 20px 22px;
      span {
        font-size: 16px;
      }
    }
  }

  &__item-flex {
    display: flex;
    align-items: center;
    gap: 16px;
    span {
      &:last-child {
        color: #1b2534;
        font-size: 22px;
        font-weight: 700;
        line-height: 321.5%;
      }
    }
    @media (max-width: 767px) {
      gap: 10px;
      span {
        &:first-child {
          width: 40px;
          height: 40px;
        }
        &:last-child {
          color: #1b2534;
          font-size: 18px;
          font-weight: 700;
          line-height: 321.5%;
        }
      }
    }
    @media (max-width: 479px) {
      span {
        &:last-child {
          font-size: 16px;
        }
      }
    }
  }

  &__form-block {
  }

  &__form {
  }

  &__form-row {
    display: grid;
    gap: 50px;
    grid-template-columns: 1fr 1fr;
    @media (max-width: 767px) {
      grid-template-columns: 1fr;
      gap: 20px;
    }
  }

  &__form-textarea {
    margin: 50px 0;
    @media (max-width: 767px) {
      margin: 20px 0;
    }
  }
}
</style>
