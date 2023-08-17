<template>
  <div class="page-map">
    <div class="page-map__container">
      <h1>
        {{ title }}
      </h1>
      <div class="page-map__flex">
        <a href="#" @click.stop.prevent="$router.push(localeLocation('/'))">
          Home
        </a>
        <base-icon icon="arrowRight" />
        <a
          v-if="link"
          href="#"
          @click.stop.prevent="$router.push(localeLocation(`/${linkTo}`))"
          class="page-map__active"
        >
          {{ link }}
        </a>
        <base-icon icon="arrowRight" />
        <span v-if="subLink" href="#" class="page-map__active">
          {{ subLink }}
        </span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    title: {
      type: String,
      default: () => null,
    },
    link: {
      type: String,
      default: () => null,
    },
    linkTo: {
      type: String,
      default: () => null,
    },
    subLink: {
      type: String,
      default: () => null,
    },
  },
}
</script>

<style lang="scss" scoped>
.page-map {
  padding: 50px 0;
  background-color: #f7f5ff;
  @media (max-width: 767px) {
		padding: 30px 0;
  }
  h1 {
    color: var(--text);
    font-size: 50px;
    font-weight: 800;
    @media (max-width: 767px) {
      font-size: 30px;
    }
    @media (max-width: 479px) {
      font-size: 22px;
    }
  }

  &__container {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  &__flex {
    display: flex;
    align-items: center;
    gap: 20px;
    a {
      color: var(--text);
      font-size: 16px;
      font-weight: 600;
    }
    @media (max-width: 767px) {
      gap: 10px;
      a {
        font-size: 14px;
      }
      .icon {
        width: 16px;
        height: 16px;
      }
    }
  }

  &__active {
    color: var(--primary) !important;
    font-size: 16px;
    font-weight: 600;
    @media (max-width: 767px) {
      font-size: 14px;
    }
  }
}
</style>
