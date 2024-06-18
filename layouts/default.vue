<template>
  <div class="page-wrap">
    <header class="header">
      <div class="wrapper">
        <div class="header__inner">
          <div class="header__item">
            <div class="header__logo">
              <TheNetwork :type="'logo'" />
            </div>
            <div class="header__link header-desktop">
              <NuxtLink to="/tariff">Тарифы</NuxtLink>
              <NuxtLink to="/contact">Контакты</NuxtLink>
            </div>
          </div>
          <div class="header__item">
            <div class="header-mobile">
              <div class="header-mobile__burger" @click="menuOpen" :class="{'is-open': isOpenMenu}" >
                <span></span>
                <span></span>
                <span></span>
              </div>
              <div class="header-mobile__drop" :class="{'is-open': isOpenMenu}">
                <div class="header-mobile__inner" :class="{'is-open': isOpenMenu}">
                  <NuxtLink to="tel:+7495118-44-22">+7 495 118-44-22</NuxtLink>
                  <NuxtLink to="/tariff">Тарифы</NuxtLink>
                  <NuxtLink to="/contact">Контакты</NuxtLink>
                  <div class="header-mobile__btns">
                    <UITheButton 
                      :label="'Вход'"
                      class="btn-transparent"
                      @click.prevent="isModalLogIn = true"
                    />
                    <UITheButton 
                      :label="'Регистрация'"
                      class="btn-dark"
                      @click.prevent="isModalSigUp = true"
                    />
                  </div>
                </div>
              </div>
            </div>
            <div class="header-desktop">
              <div class="header__phone">
                <NuxtLink to="tel:+7495118-44-22">+7 495 118-44-22</NuxtLink>
              </div>
              <div class="header__btns">
                <UITheButton 
                  :label="'Вход'"
                  class="btn-transparent"
                  @click.prevent="isModalLogIn = true"
                />
                <UITheButton 
                  :label="'Регистрация'"
                  class="btn-dark"
                  @click.prevent="isModalSigUp = true"
                />
              </div>
            </div>
            
            
          </div>
        </div>
      </div>
      <the-modal-log-in v-if="isModalLogIn" @close="closeModal"></the-modal-log-in>
      <the-modal-sig-up v-if="isModalSigUp" @close="closeModal"></the-modal-sig-up>
    </header>
    <slot />
  </div>
</template>

<script>
import TheModalLogIn from '~/components/modal/TheModalLogIn.vue'
import TheModalSigUp from '~/components/modal/TheModalSigUp.vue'
  export default {
  components: { TheModalSigUp, TheModalLogIn },
    data() {
      return {
        isOpenMenu: false,
        isModalSigUp: false,
        isModalLogIn: false,
      }
    },
    methods: {
      menuOpen() {
        if (!this.isOpenMenu) document.body.classList.add('menu-open')
        else document.body.classList.remove('menu-open')
        this.isOpenMenu = !this.isOpenMenu
      },
      closeModal() {
        this.isModalSigUp = false
        this.isModalLogIn = false
      },
    }
  }
</script>

<style lang="scss">
.header {
  background: linear-gradient(to right, #000 30%, #1C2734 74%);
  padding: 20px 0;
  &__inner {
    justify-content: space-between;
    display: flex;
    align-items: center;
  }
  &__item {
    display: flex;
    align-items: center;
    a {
      color: #fff;
    }
  }
  &__link {
    
    a {
      font-size: 18px;
      margin-left: 30px;
    }
  }
  &__btns {
    @media(max-width: 1023px) {
      width: 100%;
    }
    button  {
      margin-left: 10px;
      @media(max-width: 1023px) {
        display: block;
        text-align: center;
        width: 100%;
        margin-left: 0;
        margin-top: 10px;
      }
    }
  }
  &__phone {
    a {
      font-weight: 700;
      font-size: 18px;
      text-align: left;
      display: inline-block;
    }
  }
}
.header-desktop {
  display: flex;
  align-items: center;
  @media(max-width: 1023px) {
    display: none;
  }
}
.header-mobile {
  &__inner {
    a {
      margin-bottom: 15px;
      font-size: 18px;
      display: inline-block;
    }
      &.is-open {
        display: flex;
        flex-direction: column;
        padding: 70px 20px 50px; 
        height: 100%;
      }
    }
  &__drop {
    display: none;
    &.is-open {
      display: block;
      position: fixed;
      top: 0;
      right: 0;
      bottom: 0;
      background: linear-gradient(to top, #000 30%, #1C2734 74%);
      width: 100%;
      max-width: 300px;
      z-index: 5;
    }
  }
  &__burger {
    width: 40px;
    height: 20px;
    flex-direction: column;
    justify-content: space-between;
    cursor: pointer;
    transition: 0.3s;
    position: relative;
    display: none;
    z-index: 150;
    @media(max-width: 1023px) {
      display: flex;
    }
    span {
      display: block;
      transition: 0.3s;
      width: 100%;
      height: 3px;
      border-radius: 20px;
      background-color: #fff;
    }
    &.is-open {
      transform: rotate(180deg);
      span {
        position: absolute;
        left: 0;
        top: 50%;
        &:first-child {
          transform: rotate(45deg);
        }
        &:nth-child(2) {
          display: none;
        }
        &:last-child {
          transform: rotate(-45deg);
        }
      }
    }
  }
  &__btns {
    button {
      display: block;
      width: 100%;
      margin-top: 10px;
    }
  }
}
</style>