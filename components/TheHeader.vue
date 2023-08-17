<template>
  <header class="header">
    <div class="header__head">
      <div class="header__container">
        <a href="tel:+93365XXXXXX" class="header__head-row">
          <base-icon icon="call"></base-icon>
          <span>+(933 65) XX XX XX</span>
        </a>
        <a href="mailto: kitaphanam.com@gmail.com" class="header__head-row">
          <base-icon icon="mail"></base-icon>
          <span>kitaphanam.com@gmail.com</span>
        </a>
      </div>
    </div>
    <div class="header__fixing">
      <div class="header__body">
        <div class="header__body-row _container">
          <nuxt-link to="/" class="header__logo">
            <img src="@/assets/img/logo.png" alt="logo" />
          </nuxt-link>
          <nuxt-link to="/" class="header__logo-mobile">
            <img src="@/assets/icons/logo.svg" alt="" />
          </nuxt-link>
          <div class="header__input">
            <base-icon icon="search" class="header__input-abs-icon"></base-icon>
            <input type="text" placeholder="Search books..." />
            <button class="header__input-button">
              <base-icon icon="search"></base-icon>
            </button>
          </div>
          <div class="burger-wrapper" @click.stop="showBody">
            <button
              type="submit"
              :class="['burger', { _active: isBodyActive }]"
            >
              <span></span>
              <span></span>
              <span></span>
            </button>
          </div>
          <div class="header__languages">
            <div class="header__languages-active">
              <nuxt-link
                v-for="locale in selectedLocale"
                :key="locale.code"
                :to="switchLocalePath(locale.code)"
                >{{ locale.name }}</nuxt-link
              >
              <base-icon icon="arrowDown"></base-icon>
            </div>
            <ul class="header__languages-list">
              <li class="header__languages-item">
                <nuxt-link
                  v-for="locale in availableLocales"
                  :key="locale.code"
                  exact
                  :to="switchLocalePath(locale.code)"
                  class="header__languages-link"
                  >{{ locale.name }}</nuxt-link
                >
              </li>
            </ul>
          </div>
        </div>
      </div>
      <div class="header__footer">
        <div class="_container">
          <div class="header__footer-row">
            <button
              :class="['header__footer-categories', { _active: isCategories }]"
              @click.stop="isCategories = !isCategories"
            >
              <div class="header__footer-categories-row">
                <base-icon icon="categories" />
                <span>categories</span>
                <base-icon icon="arrowDown2" />
              </div>
              <ul class="header__footer-categories-list">
                <li class="header__footer-categories-item">
                  <nuxt-link to="/" class="header__footer-categories-link">
                    Ertekiler
                  </nuxt-link>
                </li>
                <li class="header__footer-categories-item">
                  <nuxt-link to="/" class="header__footer-categories-link">
                    Trendlar
                  </nuxt-link>
                </li>
                <li class="header__footer-categories-item">
                  <nuxt-link to="/" class="header__footer-categories-link">
                    Audio books
                  </nuxt-link>
                </li>
              </ul>
            </button>
            <nav :class="['menu', { _active: isBodyActive }]">
              <div class="menu__body-wrapper" @click.stop="closeBody">
                <div class="menu__body" @click.stop>
                  <div class="burger-wrapper white" @click.stop="showBody">
                    <button
                      type="submit"
                      :class="['burger white', { _active: isBodyActive }]"
                    >
                      <span></span>
                      <span></span>
                      <span></span>
                    </button>
                  </div>
                  <div class="categories-mobile">
                    <div class="categories-mobile__title-block">
                      <base-icon icon="categories" />
                      <span>categories</span>
                      <base-icon icon="arrowDown2" />
                    </div>
                    <ul class="categories-mobile__list">
                      <li class="categories-mobile__item">
                        <nuxt-link to="/" class="categories-mobile__link"
                          >Ertekiler</nuxt-link
                        >
                      </li>
                      <li class="categories-mobile__item">
                        <nuxt-link to="/" class="categories-mobile__link"
                          >Horrors</nuxt-link
                        >
                      </li>
                      <li class="categories-mobile__item">
                        <nuxt-link to="/" class="categories-mobile__link"
                          >Fantastic</nuxt-link
                        >
                      </li>
                    </ul>
                  </div>
                  <ul class="menu__list">
                    <li class="menu__item" v-for="link in links" :key="link.id">
                      <a
                        href="#"
                        @click.stop.prevent="goPage(link)"
                        :class="[
                          'menu__link',
                          { active: linkActiveId === link.id },
                        ]"
                      >
                        {{ link.name }}
                      </a>
                    </li>
                  </ul>
                  <div class="header__languages-mobile">
                    <ul class="header__languages-mobile-list">
                      <div class="header__languages-mobile-active">
                        <nuxt-link
                          v-for="locale in selectedLocale"
                          :key="locale.code"
                          :to="switchLocalePath(locale.code)"
                          >{{ locale.name }}</nuxt-link
                        >
                      </div>
                      <nuxt-link
                        v-for="locale in availableLocales"
                        :key="locale.code"
                        exact
                        :to="switchLocalePath(locale.code)"
                        class="header__languages-mobile-link"
                        >{{ locale.name }}</nuxt-link
                      >
                    </ul>
                  </div>
                </div>
              </div>
            </nav>
          </div>
        </div>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  data() {
    return {
      isCategories: null,
      linkActiveId: null,
      isBodyActive: null,
      links: [
        {
          id: 1,
          to: '/',
          name: 'Home',
        },
        {
          id: 2,
          to: '/about-us',
          name: 'About Us',
        },
        {
          id: 3,
          to: '/news',
          // path: ['/news', '/news/:id'],
          name: 'News',
        },
        {
          id: 4,
          to: '/contact-us',
          name: 'Contact us',
        },
      ],
    }
  },

  watch: {
    // $route: function (val) {
    //   if (val.name === `news-id___${this.$i18n.locale}`) {
    //     this.activeId = 4
    //     this.$cookie.set('activeId', 4)
    //   }
    // },
  },

  mounted() {
    if (this.$cookie.get('activeId')) {
      this.linkActiveId = Number(this.$cookie.get('activeId'))
    } else {
      this.linkActiveId = 1
    }
    const dropdownBody = document.querySelector('.header__footer-categories')
    document.addEventListener('click', (event) => {
      const isClickInside = dropdownBody?.contains(event.target)
      if (!isClickInside) {
        this.isCategories = false
      }
    })
    // let className = 'scroll'
    // let scrollTrigger = 1
    // let wrapper = document.querySelector('.wrapper')
    // wrapper.onscroll = function () {
    //   if (
    //     wrapper.scrollTop >= scrollTrigger ||
    //     window.pageYOffset >= scrollTrigger
    //   ) {
    //     document.querySelector('.header').classList.add(className)
    //   } else {
    //     document.querySelector('.header').classList.remove(className)
    //   }
    // }
    // wrapper.addEventListener('scroll', (e) => {
    //   if (e.target.scrollTop > 30) {
    //     this.header = true
    //   } else {
    //     this.header = false
    //   }
    // })
  },

  methods: {
    goPage(path) {
      this.linkActiveId = path.id
      this.$cookie.set('activeId', path.id)
      this.isBodyActive = false
      this.$router.push(this.localeLocation(path.to))
      if (document.querySelector('.wrapper').classList.contains('_lock')) {
        document.querySelector('.wrapper').classList.remove('_lock')
      }
    },
    showBody() {
      if (document.querySelector('.wrapper').classList.contains('_lock')) {
        document.querySelector('.wrapper').classList.remove('_lock')
      } else {
        document.querySelector('.wrapper').classList.add('_lock')
      }
      this.isBodyActive = !this.isBodyActive
    },
    closeBody() {
      document.querySelector('.wrapper').classList.remove('_lock')
      this.isBodyActive = false
    },
  },

  computed: {
    availableLocales() {
      return this.$i18n.locales.filter((i) => i.code !== this.$i18n.locale)
    },
    selectedLocale() {
      return this.$i18n.locales.filter((i) => i.code === this.$i18n.locale)
    },
  },
}
</script>

<style lang="scss" scoped>
.header {
  position: sticky;
  top: -40px;
  left: 0;
  width: 100%;
  z-index: 100;
  box-shadow: 0.5px 0.5px 5px;
  @media (max-width: 767px) {
    top: -30px;
  }
  &.scroll {
    .header__head {
      height: 0;
      width: 0;
    }
  }
  // .header__head

  &__head {
    height: 40px;
    background-color: var(--black2);
    transition: all 0.1s ease 0s;
    @media (max-width: 767px) {
      height: 30px;
    }
  }

  &__container {
    display: flex;
    align-items: center;
    height: 100%;
    gap: 40px;
    @media (max-width: 767px) {
      gap: 20px;
    }
  }

  // .header__head-row

  &__head-row {
    display: flex;
    align-items: center;
    gap: 6px;
    span {
      color: #fff;
      transition: all 0.3s ease 0s;
      font-size: 12px;
      font-weight: 400;
    }
    &:hover {
      span {
        color: orange;
      }
    }
    @media (max-width: 767px) {
      span {
        gap: 4px;
        font-size: 10px;
      }
    }
  }

  &__fixing {
    background-color: #fff;
    box-shadow: 0.2px 0.2px 0.5px;
  }

  // .header__body

  &__body {
    padding: 15px 0;
    @media (max-width: 767px) {
      padding: 10px 0 6px;
    }
  }

  &__body-row {
    display: flex;
    align-items: center;
  }

  // .header__logo

  &__logo {
    height: 36px;
    &:not(:last-child) {
      margin-right: 100px;
    }
    img {
      height: 100%;
    }
    @media (max-width: 1100px) {
      &:not(:last-child) {
        margin-right: 60px;
      }
    }
    @media (max-width: 767px) {
      display: none;
    }
  }

  &__logo-mobile {
    width: 30px;
    min-height: 25px;
    img {
      width: 100%;
      height: 100%;
    }
    @media (min-width: 767px) {
      display: none;
    }
  }

  // .header__input

  &__input {
    width: 100%;
    height: 40px;
    flex: 1 1 auto;
    position: relative;
    margin-right: 300px;
    input {
      width: 100%;
      height: 100%;
      border: 1px solid var(--dark-border);
      background-color: var(--border);
      border-radius: 50px;
      padding: 14px 20px 14px 50px;
      font-size: 16px;
      color: var(--text);
      transition: 0.3s ease 0s;
      &::placeholder {
        color: var(--icon-color);
      }
      &:focus {
        box-shadow: 0.2px 0.2px 3px;
        border: 1px solid var(--primary);
      }
    }
    @media (max-width: 1100px) {
      margin-right: 150px;
    }
    @media (max-width: 767px) {
      height: 30px;
      margin: 0 14px 0 14px;
      input {
        border-radius: 10px;
        font-size: 14px;
        padding-left: 10px;
      }
    }
  }

  // .header__input-abs-icon

  &__input-abs-icon {
    position: absolute;
    left: 14px;
    top: 50%;
    transform: translateY(-50%);
    color: var(--icon-color);
    pointer-events: none;
    @media (max-width: 767px) {
      left: auto;
      width: 20px;
      height: 20px;
      right: 10px;
    }
  }

  // .header__input-button

  &__input-button {
    position: absolute;
    background-color: var(--primary);
    color: #fff;
    width: 90px;
    height: 40px;
    border-radius: 50px;
    top: 50%;
    transform: translateY(-50%);
    right: 0;
    cursor: pointer;
    transition: all 0.1s ease 0s;
    &:active {
      margin-top: 1px;
    }
    @media (max-width: 767px) {
      width: 41px;
      height: 30px;
      border-radius: 10px;
      display: none;
      span {
        &:deep(svg) {
          width: 20px;
          height: 20px;
        }
      }
    }
  }

  // .header__languages

  &__languages {
    position: relative;
    &:hover {
      .header__languages-list {
        opacity: 1;
        visibility: visible;
        transform: translateY(0px);
      }
    }
    @media (max-width: 767px) {
      display: none;
    }
  }

  // .header__languages-active

  &__languages-active {
    display: flex;
    align-items: center;
    gap: 10px;
    cursor: pointer;
    font-size: 16px;
    line-height: calc(19 / 16 * 100%);
    font-weight: 700;
  }

  // .header__languages-list

  &__languages-list {
    position: absolute;
    box-shadow: 0.2px 0.2px 5px;
    width: 100%;
    right: 0;
    border-radius: 6px;
    transition: all 0.3s ease 0s;
    opacity: 0;
    visibility: hidden;
    transform: translateY(-10px);
    padding: 5px;
  }

  // .header__languages-item

  &__languages-item {
    background-color: #fff;
    border-radius: 6px;
  }

  // .header__languages-link

  &__languages-link {
    display: block;
    color: var(--text);
    font-size: 16px;
    line-height: calc(19 / 16) * 100%;
    font-weight: 700;
    width: 100%;
    padding: 4px;
    transition: all 0.3s ease 0s;
    &:hover {
      background-color: #e5e5e5;
      color: var(--primary);
    }
  }

  // .header__footer

  &__footer {
  }

  &__footer-row {
    display: flex;
    align-items: center;
    padding-bottom: 10px;
    @media (max-width: 767px) {
      justify-content: space-between;
      gap: 20px;
      padding-bottom: 6px;
    }
  }

  // .header__footer-categories

  &__footer-categories {
    width: 257px;
    height: 40px;
    border-radius: 20px;
    cursor: pointer;
    background-color: var(--primary);
    margin-right: 185px;
    position: relative;
    transition: 0.1s ease 0s;
    user-select: none;
    &:active {
      transform: scale(1.01);
    }
    &._active {
      border-radius: 20px 20px 5px 5px;
      border-bottom: 2px solid #fff;
      .header__footer-categories-list {
        opacity: 1;
        visibility: visible;
      }
      .header__footer-categories-row {
        span {
          &:last-child {
            transform: rotate(180deg);
          }
        }
      }
    }
    @media (max-width: 1100px) {
      margin-right: 80px;
    }
    @media (max-width: 767px) {
      width: 160px;
      margin: 0;
      height: 28px;
      display: none;
    }
  }

  // .header__footer-categories-row

  &__footer-categories-row {
    user-select: none;
    display: flex;
    align-items: center;
    padding: 10px 20px;
    width: 100%;
    height: 100%;
    span {
      color: #fff;
      font-size: 16px;
      font-weight: 600;
      transform: 0.3s ease 0s;
      display: flex;
      align-items: center;
      &:first-child {
        margin-right: 10px;
      }
      &:nth-child(2) {
        flex: 1 1 auto;
        text-align: left;
      }
    }
    @media (max-width: 767px) {
      padding: 4px 14px;
      span {
        color: #fff;
        font-size: 14px;
        font-weight: 600;
        transform: 0.3s ease 0s;
        &:first-child {
          margin-right: 6px;
          width: 20px;
          height: 20px;
        }
      }
    }
  }

  // .header__footer-categories-list

  &__footer-categories-list {
    position: absolute;
    width: calc(100% - 2px);
    background-color: #fff;
    box-shadow: 0.2px 0.2px 5px;
    border-radius: 5px 5px 8px 8px;
    top: calc(100% + 2px);
    left: 50%;
    transform: translateX(-50%);
    transition: opacity 0.1s ease 0s;
    opacity: 0;
    visibility: hidden;
    z-index: 10;
  }

  // .header__footer-categories-item

  &__footer-categories-item {
    &:not(:last-child) {
      border-bottom: 1px solid #e5e5e5;
    }
  }

  // .header__footer-categories-link

  &__footer-categories-link {
    display: block;
    text-align: left;
    padding: 6px 12px;
    transition: all 0.3s ease 0s;
    font-size: 16px;
    font-weight: 500;
    border-bottom: 1px solid #e5e5e5;

    &:hover {
      background-color: #e5e5e5;
      color: var(--primary);
    }
    @media (max-width: 767px) {
      font-size: 14px;
    }
  }
}
.menu {
  &._active {
    .menu__body-wrapper {
      left: 0;
      transition: all 0.3s;
    }
    .menu__body {
      transition: all 0.3s;
      left: 0;
    }
  }
  &__body-wrapper {
    @media (max-width: 767px) {
      position: fixed;
      left: -100%;
      top: 0;
      height: 100vh;
      width: 100%;
      position: fixed;
      background-color: rgba(0, 0, 0, 0.2);
      backdrop-filter: blur(3px);
      width: 100%;
      height: 100%;
      z-index: 500;
      transition: all 0.3s;
    }
  }

  // .menu__body

  &__body {
    @media (max-width: 767px) {
      position: fixed;
      left: -100%;
      width: 70%;
      height: 100%;
      background: var(--black);
      transition: all 0.3s ease 0s;
      display: flex;
      flex-direction: column;
    }
  }

  // .menu__list

  &__list {
    display: flex;
    gap: 60px;
    @media (max-width: 1100px) {
      gap: 40px;
    }
    @media (max-width: 767px) {
      flex-direction: column;
      padding: 0 30px 0;
      flex: 1 1 auto;
    }
  }

  // .menu__item

  &__item {
  }

  // .menu__link

  &__link {
    color: var(--text);
    font-size: 16px;
    font-weight: 600;
    transition: 0.3s ease 0s;
    cursor: pointer;
    padding-bottom: 2px;
    white-space: nowrap;
    &:hover {
      color: var(--primary);
    }
    &.active {
      color: var(--primary);
      border-bottom: 1px solid var(--primary);
    }
    @media (max-width: 767px) {
      display: block;
      font-size: 18px;
      color: rgba(255, 255, 255, 0.5);
      padding-bottom: 5px;
      width: 80%;
      &:hover {
        color: #fff;
      }
      &.active {
        color: var(--white);
        border-bottom: 1px solid var(--white);
      }
    }
  }
}
.burger-wrapper {
  @media (max-width: 767px) {
    background-color: transparent;
    width: 26px;
    height: 26px;
    display: flex;
    justify-content: center;
    align-items: center;
    border-radius: 4px;
    position: relative;
    z-index: 10;
    margin-right: 8px;
    &.white {
      margin: 0 0 0 auto;
      padding: 30px;
      justify-content: flex-end;
    }
  }
  @media (max-width: 479px) {
    margin: -1px;
  }
}
.burger {
  display: none;
  @media (max-width: 767px) {
    display: block;
    cursor: pointer;
    min-width: 24px;
    height: 16px;
    position: relative;
    z-index: 102;
    background-color: transparent;
    display: flex;
    justify-content: center;
    &.white {
      min-width: 28px;
      height: 18px;
      span {
        background-color: #fff;
      }
    }
  }
  span {
    transition: 0.3s;
    height: 3.4px;
    position: absolute;
    border-radius: 10px;
    background-color: #111214;
    transition: 0.1s;
    &:nth-child(1) {
      top: 0;
      width: 100%;
      transition: 0.1s;
    }
    &:nth-child(2) {
      top: calc(50% - 1px);
      width: 100%;
      transition: 0.1s;
    }
    &:nth-child(3) {
      top: calc(100% - 2px);
      width: 100%;
      transition: 0.1s;
    }
  }
  &.active {
    span {
      transition: 0.1s;
      &:nth-child(1) {
        top: 50%;
        transform: rotate(45deg);
      }
      &:nth-child(2) {
        display: none;
      }
      &:nth-child(3) {
        transform: rotate(-45deg);
        top: 50%;
      }
    }
  }
}
.header {
  &__languages-mobile {
    display: none;
    padding-bottom: 40px;
    @media (max-width: 767px) {
      display: block;
    }
  }

  &__languages-mobile-active {
    color: #111214;
    background-color: #fff;
    font-size: 16px;
    font-style: normal;
    font-weight: 700;
    padding: 10px;
    border-radius: 14px;
    min-width: 70px;
    text-align: center;
  }

  &__languages-mobile-list {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 10px;
  }

  &__languages-mobile-link {
    color: #111214;
    background: rgba(255, 255, 255, 0.1);
    font-size: 16px;
    font-style: normal;
    font-weight: 700;
    padding: 10px;
    border-radius: 14px;
    min-width: 70px;
    text-align: center;
    color: #fff;
  }
}
.categories-mobile {
  padding: 40px 30px 40px;
  display: none;
  @media (max-width: 767px) {
    display: block;
  }
  &.active {
    .categories-mobile__list {
      height: auto;
    }
  }
  &__title-block {
    display: flex;
    align-items: center;
    gap: 10px;
    color: #fff;
    font-size: 20px;
    font-weight: 600;
  }

  &__list {
    display: flex;
    flex-direction: column;
    gap: 20px;
    padding-top: 20px;
    display: none;
  }

  &__item {
  }

  &__link {
    font-size: 18px;
    font-style: normal;
    font-weight: 600;
    color: #fff;
    padding-left: 10px;
  }
}
</style>
