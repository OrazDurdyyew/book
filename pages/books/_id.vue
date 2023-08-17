<template>
  <div class="book-details">
    <base-page-map
      title="Product Details"
      link="Books"
      linkTo="books"
      subLink="Book"
    />
    <div class="book-details__container">
      <div class="book-details__row">
        <div class="book-details__image">
          <img src="@/assets/img/book_3.png" alt="" />
        </div>
        <div class="book-details__content">
          <h2 class="book-details__title">The Girl and the Last Sleeoover</h2>
          <div class="book-details__content-flex">
            <div class="flex gap-6">
              <span>Author:</span>
              <span class="bold">Suzanne Casey </span>
              <span class="none">|</span>
            </div>
            <div class="flex gap-6">
              <span class="none">|</span>
              <span>Language:</span>
              <span class="bold">English</span>
            </div>
            <div class="flex gap-6">
              <span>Category:</span>
              <span class="bold">Ertekiler</span>
              <span class="none">|</span>
            </div>
            <div class="flex gap-6">
              <span>Page:</span>
              <span class="bold">312</span>
              <span class="none">|</span>
            </div>
            <div class="flex gap-6 flex-y-center">
              <base-icon icon="redLikeBig" />
              <span class="bold">312</span>
            </div>
          </div>
          <div class="book-details__button-wrapper">
            <button
              v-for="button in buttons"
              :key="button.id"
              @click="selectedId = button.id"
              :class="[
                'book-details__button',
                { active: selectedId === button.id },
              ]"
            >
              {{ button.title }}
            </button>
          </div>
          <p class="book-details__description">
            The standard Lorem Ipsum passage is: Lorem ipsum dolor sit amet,
            consectetur adipiscing elit, sed do eiusmod tempor incididunt ut
            labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud
            exercitation ullamco laboris nisi ut aliquip ex ea commodo
            consequat.The standard Lorem Ipsum passage is: Lorem ipsum dolor sit
            amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt
            ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis
            nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo
            consequat.
          </p>
          <div class="book-details__button-wrapper">
            <base-button>Ýükläp al</base-button>
            <base-button transparent>Okamak</base-button>
          </div>
          <div class="book-details__button-wrapper">
            <div class="book-details__icon-flex">
              <base-icon icon="downloadIcon" />
              <span>540</span>
            </div>
            <div class="book-details__icon-flex">
              <base-icon icon="eyeIcon" />
              <span>5401</span>
            </div>
          </div>
        </div>
      </div>
      <the-trending-books background></the-trending-books>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      selectedId: 1,
      buttons: [
        {
          id: 1,
          title: 'AUDIO',
        },
        {
          id: 2,
          title: 'EBOOK',
        },
      ],
    }
  },
}
</script>

<style lang="scss" scoped>
.book-details {
  &__container {
  }

  &__row {
    margin-top: 70px;
    display: grid;
    grid-template-columns: minmax(250px, 362px) 1fr;
    gap: 40px;
    height: 514px;
    @media (max-width: 992px) {
      grid-template-columns: 1fr;
      height: auto;
      margin-top: 40px;
      gap: 20px;
    }
  }

  &__image {
    width: 100%;
    height: 100%;
    padding: 20px;
    border-radius: 16px;
    border: 1px solid rgba(51, 51, 51, 0.3);
    transition: all 0.2s ease 0s;
    img {
      width: 100%;
      height: 100%;
      transition: all 0.2s ease 0s;
    }
    &:hover {
      img {
        transform: scale(1.05);
      }
    }
    @media (max-width: 992px) {
      text-align: center;
      img {
        width: 300px;
        height: 400px;
        margin: 0 auto;
      }
    }
    @media (max-width: 767px) {
      text-align: center;
      img {
        width: 250px;
        height: 350px;
        margin: 0 auto;
      }
    }
    @media (max-width: 400px) {
      img {
        width: 200px;
        height: 300px;
        margin: 0 auto;
      }
    }
  }

  &__content {
    border-radius: 16px;
    border: 1px solid rgba(51, 51, 51, 0.3);
    padding: 20px;
    display: flex;
    flex-direction: column;
    gap: 30px;
    @media (max-width: 767px) {
      gap: 15px;
    }
  }

  &__title {
    color: var(--text);
    font-size: 40px;
    font-weight: 800;
    @media (max-width: 767px) {
      font-size: 26px;
    }
  }

  &__content-flex {
    display: flex;
    align-items: center;
    gap: 10px;
    span {
      color: #3333335d;
      font-size: 16px;
      font-weight: 800;
      &.bold {
        color: #33333391;
      }
    }
    .icon {
      &:active {
        transform: scale(1.2);
      }
    }
    @media (max-width: 767px) {
      gap: 14px;
      flex-direction: column;
      align-items: flex-start;
      span {
        font-size: 14px;
      }
      .none {
        display: none;
      }
      .icon {
        width: 28px;
        height: 28px;
      }
    }
  }

  &__button-wrapper {
    display: flex;
    align-items: center;
    gap: 20px;
  }

  &__button {
    padding: 7px 20px;
    background-color: #f7f5ff;
    display: flex;
    align-items: center;
    cursor: pointer;
    color: var(--text);
    font-size: 18px;
    font-weight: 500;
    border-radius: 10px;
    border: 1px solid transparent;
    &.active {
      color: var(--primary);
      border: 1px solid var(--primary);
    }
    &:active {
      transform: scale(1.1);
    }
  }

  &__description {
    color: #33333367;
    font-size: 18px;
    font-weight: 600;
    line-height: 140%;
    text-align: justify;
  }

  &__icon-flex {
    display: flex;
    align-items: center;
    gap: 6px;
    span {
      &:first-child {
        color: var(--text);
      }
      &:last-child {
        color: #33333391;
        font-size: 16px;
        font-weight: 800;
      }
    }
  }
}
</style>
