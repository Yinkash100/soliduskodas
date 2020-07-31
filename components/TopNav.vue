<template>
  <div class="nav">
    <div class="navbar" :class="colorNav">
      <div class="navbar__left">
        <div class="navbar__logo">
          <img
            v-if="!sideNavIsOpen"
            src="icons/logo.svg"
            height="33"
            width="169"
            class="navbar__logo-img"
          />
          <img
            v-else
            src="icons/whitelogo.svg"
            height="33"
            width="169"
            class="navbar__logo-img"
          />
        </div>
      </div>
      <div class="navbar__right">
        <div class="navbar__language">
          <button class="btn" :class="topNavBtn">
            Eng <font-awesome-icon icon="caret-down" />
          </button>
        </div>
        <div class="navbar__toggle" @click="toggleSideNav">
          <img
            v-if="!sideNavIsOpen"
            src="icons/menu.png"
            height="25"
            width="32"
            class="navbar__toggle-icon"
          />
          <img
            v-else
            src="icons/cancel.svg"
            height="25"
            width="32"
            class="navbar__toggle-icon"
          />
        </div>
      </div>
    </div>
    <div v-if="sideNavIsOpen" class="navdrop">
      <ul class="navdrop__link">
        <li class="navdrop__link-item">
          <nuxt-link to="/" exact>Home</nuxt-link>
        </li>
        <li class="navdrop__link-item">
          <nuxt-link to="/services">Services</nuxt-link>
        </li>
        <li class="navdrop__link-item">
          <nuxt-link to="/clients">Clients</nuxt-link>
        </li>
        <li class="navdrop__link-item">
          <nuxt-link to="/works">Works</nuxt-link>
        </li>
        <li class="navdrop__link-item">
          <nuxt-link to="/about">About</nuxt-link>
        </li>
        <li class="navdrop__link-button"></li>
      </ul>
      <div class="navdrop__button">
        <button class="btn btn--primary navdrop__button--btn">
          Free consultation
          <font-awesome-icon icon="arrow-right" />
        </button>
      </div>
      <div class="navdrop__contact">
        <ul class="navdrop__contact--group">
          <li class="navdrop__contact--group-item">
            <a href="tel:+37064052717"
              ><font-awesome-icon icon="phone-alt" /> +370 640 52717</a
            >
          </li>
          <li class="navdrop__contact--group-item-mail">
            <a href="mailto:info@soliduskodas.lt"
              ><font-awesome-icon :icon="['far', 'envelope']" />
              info@soliduskodas.lt</a
            >
          </li>
          <li class="navdrop__contact--group-item-address">
            UAB “Solidus kodas <br />Į. k. 304447806 <br />PVM kodas:
            LT100011161011 <br />Pramonės g. 15, Šiauliai
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "TopNav.vue",
  data() {
    return {
      sideNavIsOpen: false,
      colorNav: "bg-white",
      topNavBtn: 'btn--outline'
    };
  },
  methods: {
    toggleSideNav() {
      this.sideNavIsOpen = !this.sideNavIsOpen;
      this.colorNav =
        this.sideNavIsOpen === false ? "bg-white" : "bg-secondary";
      this.topNavBtn === this.sideNavIsOpen === false ? "btn--outline" : "btn--text";
    }
  }
};
</script>

<style scoped lang="scss">
.navbar {
  display: flex;
  flex-wrap: nowrap;
  justify-content: space-between;
  width: 100%;
  padding: 0.5rem;
  @include respond(tab-land) {
    padding: 1rem;
    &__logo-img {
      height: 150%;
    }
  }

  &__right {
    display: flex;
    flex-wrap: nowrap;
    justify-content: flex-end;
  }
  &__language {
    display: none;
    @include respond(tab-land) {
      display: block;
      margin-right: 1rem;
    }
  }
  &__toggle {
    &-icon {
      display: inline-block;
      // margin: 0 0.5rem;
      color: $color-primary;
    }
  }
}
.navdrop {
  display: block;
  position: absolute;
  top: 3rem;
  width: 100%;
  background-color: $color-secondary;
  color: $color-white;
  padding: 0.5rem;

  @include respond(tab-land){
    top: 0;
    color: $color-black-deep;
    background-color: $color-secondary;
    background-position: top;
    -webkit-clip-path: polygon(0 0, 12.5% 0, 25% 100%, 0% 100%);
    clip-path: polygon(0 0, 12.5% 0, 25% 100%, 0% 100%);

    &__toggle-icon{
     color: $color-black-deep;
    }
  }
  &__toggle-icon{
    color: $color-white;
  }
  &__link {
    text-align: center;
    padding: 0.5rem 0 1rem;
    &-item {
      font-size: 1.2rem;
      padding: 1rem;
      font-weight: bolder;
    }
  }
  &__button {
    &--btn {
      padding: 1rem 0;
      width: 100%;
    }
  }
  &__contact {
    text-align: center;
    padding: 1rem 0 3rem;

    &--group {
      &-item {
        line-height: 1.75rem;
        &-mail {
          font-weight: bold;
          margin-bottom: 0.5rem;
        }
        &-address {
          line-height: 1.4rem;
        }
      }
    }
  }

}
.bg-white {
  background-color: $color-white;
}
.bg-secondary {
  background-color: $color-secondary;
  @include respond(tab-land){
    background-color: $color-white;
  }
}
</style>
