<template>
  <footer class="footer">
    <div class="footer__container">
      <div class="footer__logo-wrapper flex flex-sb">
        <div class="footer__logo">
          <img src="@/assets/img/logo-footer.svg" alt="" />
        </div>
        <nav class="footer-menu">
          <ul class="footer-menu__list">
            <li class="footer-menu__item" v-for="link in links" :key="link.id">
              <a
                @click.stop.prevent="goPage(link)"
                :to="link.to"
                :class="[
                  'footer-menu__link',
                  { active: linkActiveId == link.id },
                ]"
              >
                {{ link.name }}
              </a>
            </li>
          </ul>
        </nav>
      </div>
      <div class="footer__about-wrapper flex flex-y-center">
        <div class="footer__about-empty"></div>
        <div class="footer__about flex flex-y-center">
          <div>
            <h4 class="footer__about-title">E-mail poçta:</h4>
            <a
              href="mailto: kitaphanam.com@gmail.com"
              class="footer__about-flex flex gap-4 flex-y-center"
            >
              <base-icon icon="mail" class="footer__about-icon" />
              <span class="footer__about-text">kitaphanam.com@gmail.com</span>
            </a>
          </div>
          <div>
            <h4 class="footer__about-title">Telefon belgimiz:</h4>
            <a
              href="tel:+99365000000"
              class="footer__about-flex flex gap-4 flex-y-center"
            >
              <base-icon icon="call" class="footer__about-icon" />
              <span class="footer__about-text">+993 65 00 00 00</span>
            </a>
          </div>
        </div>
      </div>
    </div>
    <div class="footer__bottom">
      <div class="footer__container-row">
        <p></p>
        <p>Copyrıght © BookStore. All rights reserved</p>
        <p>founded by #dob</p>
      </div>
    </div>
  </footer>
</template>

<script>
export default {
  data() {
    return {
      linkActiveId: null,
      links: [
        {
          id: 1,
          to: '/',
          name: 'Home',
        },
        {
          id: 2,
          to: '/about-us',
          name: 'About us',
        },
        {
          id: 3,
          to: '/news',
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
  mounted() {
    if (this.$cookie.get('activeId')) {
      this.linkActiveId = Number(this.$cookie.get('activeId'))
    } else {
      this.linkActiveId = 1
    }
  },

  methods: {
    goPage(path) {
      this.linkActiveId = path.id
      this.$cookie.set('activeId', path.id)
      this.$router.push(this.localeLocation(path.to))
      if (document.querySelector('.wrapper').classList.contains('_lock')) {
        document.querySelector('.wrapper').classList.remove('_lock')
      }
    },
  },
}
</script>

<style lang="scss" scoped>
.gap-60 {
  gap: 60px;
}
.footer {
  background: var(--black2);
  margin-top: 100px;
  @media (max-width: 767px) {
    margin-top: 50px;
  }
  // .footer__container

  &__container {
    padding: 60px 20px;
    @media (max-width: 767px) {
      padding: 40px 20px;
    }
  }

  &__logo-wrapper {
    @media (max-width: 767px) {
      flex-direction: column;
      gap: 20px;
    }
  }

  // .footer__logo

  &__logo {
    @media (max-width: 767px) {
      width: 200px;
      img {
        width: 100%;
      }
    }
  }

  &__about-wrapper {
    margin-top: 50px;
    @media (min-width: 767px) {
      justify-content: space-between;
    }
  }

  &__about-empty {
    @media (max-width: 767px) {
      display: none;
    }
  }

  // .footer__about

  &__about {
    display: flex;
    gap: 50px;
    @media (max-width: 767px) {
      gap: 30px;
    }
  }

  // .footer__about-title

  &__about-title {
    color: #ffffff80;
    font-size: 18px;
    font-weight: 600;
    margin-bottom: 14px;
    @media (max-width: 767px) {
      font-size: 14px;
      margin-bottom: 10px;
    }
  }

  &__about-flex {
    &:hover {
      .footer__about-icon {
        &:deep(svg) {
          color: orange;
        }
      }
      .footer__about-text {
        color: orange;
      }
    }
  }

  // .footer__about-icon

  &__about-icon {
    color: #ffffff80;
    transition: all 0.3s ease 0s;
    &:deep(svg) {
      width: 18px;
      height: 18px;
    }
  }

  // .footer__about-text

  &__about-text {
    color: #ffffff80;
    font-size: 14px;
    font-weight: 400;
    transition: all 0.3s ease 0s;
  }

  &__bottom {
    border-top: 1px solid #ffffff80;
    padding: 15px 0;
  }

  &__container-row {
    display: flex;

    p {
      color: #ffffff80;
      font-size: 16px;
      font-weight: 500;
      @media (max-width: 479px) {
        font-size: 10px;
        &:last-child {
          margin-left: 16px;
        }
      }
    }
    @media (max-width: 479px) {
      justify-content: center;
    }
    @media (min-width: 479px) {
      justify-content: space-between;
    }
  }
}
.footer-menu {
  display: flex;
  align-items: center;
  // .footer-menu__list

  &__list {
    display: flex;
    align-items: center;
    gap: 80px;
    @media (max-width: 767px) {
      gap: 40px;
    }
    @media (max-width: 479px) {
      gap: 14px;
      flex-direction: column;
      align-items: flex-start;
    }
  }

  // .footer-menu__item

  &__item {
  }

  // .footer-menu__link

  &__link {
    color: #ffffff80;
    font-size: 18px;
    font-weight: 600;
    cursor: pointer;
    transition: 0.3s ease 0s;
    &.active {
      color: rgba(255, 255, 255, 1);
    }
    &:hover {
      color: rgba(255, 255, 255, 1);
    }
    @media (max-width: 479px) {
      font-size: 16px;
    }
  }
}
</style>
