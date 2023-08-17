<template>
  <div class="admin-sidebar">
    <nav class="admin-sidebar-menu">
      <ul class="admin-sidebar-menu__list">
        <li
          class="admin-sidebar-menu__item"
          v-for="link in links"
          :key="link.id"
        >
          <nuxt-link
            :to="`/admin${link.to}`"
            exact
            class="admin-sidebar-menu__link"
          >
            <base-icon :icon="link.icon" />
            <span>{{ link.name }}</span>
          </nuxt-link>
        </li>
      </ul>
    </nav>
  </div>
</template>

<script>
export default {
  data() {
    return {
      links: [
        {
          id: '1',
          to: '/',
          icon: 'adminBook',
          name: 'Books',
        },
        {
          id: '2',
          to: '/audio-books',
          icon: 'adminAudioBook',
          name: 'Audiobooks',
        },
        {
          id: '3',
          to: '/news',
          icon: 'adminNews',
          name: 'News',
        },
      ],
    }
  },
}
</script>

<style lang="scss" scoped>
.admin-sidebar {
  padding: 40px 15px;
  background-color: #edeff2;
}
.admin-sidebar-menu {
  &__list {
    display: flex;
    flex-direction: column;
    gap: 10px;
  }

  &__item {
  }

  &__link {
    display: flex;
    align-items: center;
    gap: 20px;
    padding: 15px;
    background-color: var(--white);
    border-radius: 10px;
    box-shadow: 0px 10px 30px 0px rgba(136, 51, 255, 0.1);
    transition: 0.1s ease 0s;
    &:hover {
      background-color: var(--primary);
      span {
        color: #fff;
        &:deep(svg) {
          color: #fff;
        }
      }
    }
    &.nuxt-link-active,
    &.nuxt-link-exact-active {
      background-color: var(--primary);
      span {
        color: #fff;
        &:deep(svg) {
          color: #fff;
        }
      }
    }
    span {
      color: var(--admin-text);
      font-size: 14px;
      font-weight: 700;
      &:deep(svg) {
        color: var(--admin-text);
      }
    }
  }
}
</style>
