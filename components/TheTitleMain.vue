<template>
  <nuxt-link to="/" class="title-main">
    <div class="title-main__title">
      <h1>{{ title }}</h1>
      <base-icon :icon="icon" class="title-main__icon" />
    </div>
    <div class="title-main__router">
      <span>View all books</span>
      <base-icon icon="navigationRight" class="title-main__route"></base-icon>
    </div>
  </nuxt-link>
</template>

<script>
export default {
  props: {
    title: {
      type: String,
      default: () => null,
    },
    icon: {
      type: String,
      default: () => null,
    },
  },
}
</script>

<style lang="scss" scoped>
.title-main {
  display: flex;
  justify-content: space-between;
  margin-bottom: 40px;
  &:hover {
    .title-main__title h1 {
      color: var(--primary);
      @media (max-width: 767px) {
      }
    }
    .title-main__icon {
      &:deep(svg) {
        color: var(--primary);
      }
    }
    .title-main__router span {
      color: var(--primary);
      @media (max-width: 767px) {
      }
    }
    .title-main__route {
      color: var(--primary);
    }
  }
  @media (max-width: 767px) {
    margin-bottom: 20px;
  }
  // .title-main__title

  &__title {
    display: flex;
    align-items: center;
    gap: 12px;
    @media (max-width: 479px) {
      gap: 8px;
    }
    h1 {
      transition: all 0.1s ease 0s;
      font-size: 36px;
      font-weight: 700;
      color: var(--text);
      @media (max-width: 767px) {
        font-size: 28px;
      }
      @media (max-width: 479px) {
        font-size: 20px;
        gap: 8px;
      }
    }
  }

  &__icon {
    width: 20px;
    height: 20px;
    &:deep(svg) {
      transition: all 0.1s ease 0s;
    }
  }

  // .title-main__router

  &__router {
    display: flex;
    align-items: center;
    gap: 10px;
    span {
      color: var(--icon-color);
      font-size: 16px;
      font-weight: 600;
      @media (max-width: 479px) {
        font-size: 12px;
      }
    }
    @media (max-width: 479px) {
			gap: 2px;
    }
  }

  // .title-main__route

  &__route {
    color: var(--icon-color);
    width: 20px;
    height: 20px;
    transform: translateX(0px);
    transition: all 0.1s ease 0s;
  }
}
</style>
