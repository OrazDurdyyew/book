<template>
  <div class="admin-header">
    <div class="admin-header__logo">
      <img src="@/assets/img/logo.png" alt="logo" />
    </div>
    <div class="admin-header__input">
      <base-icon icon="search" class="admin-header__input-abs-icon"></base-icon>
      <input type="text" placeholder="Search books..." />
      <button class="admin-header__input-button">
        <base-icon icon="search"></base-icon>
      </button>
    </div>
    <div class="admin-header__profile">
      <span>Admin</span>
      <div class="admin-header__profile-img"></div>
    </div>
  </div>
</template>

<script>
export default {}
</script>

<style lang="scss" scoped>
.admin-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 80px;
  padding: 20px;
  background-color: #edeff2;
  &__logo {
    width: 210px;
    img {
      width: 100%;
    }
  }

  &__input {
    width: 40%;
    height: 50px;
    position: relative;
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
      left: 7px;
      width: 20px;
      height: 20px;
    }
  }

  // .header__input-button

  &__input-button {
    position: absolute;
    background-color: var(--primary);
    color: #fff;
    width: 90px;
    height: 50px;
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
      span {
        &:deep(svg) {
          width: 20px;
          height: 20px;
        }
      }
    }
  }

  &__profile {
    display: flex;
    gap: 20px;
    align-items: center;
    span {
      color: var(--text);
      font-size: 16px;
      font-weight: 500;
    }
    &-img {
      width: 40px;
      height: 40px;
      border-radius: 50%;
      background-color: #444;
    }
  }
}
</style>
