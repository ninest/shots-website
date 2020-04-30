<template lang="pug">
  nav(:class="{ 'extended-width': extendedWidth }")
    .logo
      nuxt-link(to="/")
        img(src='~/assets/svg/logo.svg')
    .right
      //- nuxt-link(to="") Blog
      nuxt-link(to="/guides") Guides
      nuxt-link(to="/#features").highlight.features Features
      nuxt-link(to="/#download").highlight.install Download
</template>

<script>
export default {
  props: {
    extendedWidth: {
      default: false,
      required: false,
    }
  },
}
</script>

<style lang="scss" scoped>
nav {
  background-color: #222222;
  border-bottom: 1px solid #000000;
  display: flex;

  justify-content: space-between;
  align-items: center;

  padding: calc(var(--dense-padding) * 1.5) var(--side-padding);
  &.extended-width {
    @include desktop-screen { 
      padding: calc(var(--dense-padding) * 1.5) 10%;
    }
  }

  position: sticky;
  top: 0;

  .logo {
    img {
      height: calc(var(--font-size) * 2);
    }
  }

  font-size: 0.8em;

  .right {
    display: flex;
    align-content: center;

    & > a {
      // margin-left: var(--main-padding);

      display: block;

      color: unset;
      text-decoration: unset;

      padding: var(--dense-padding) calc(var(--dense-padding) * 3.5);
      line-height: 1.8;

      &.highlight {
        // background-color: rgb(200, 200, 200);
        background-color: #111;

        border: 1px solid var(--border-color);

        &.features {
          border-radius: 9px 0 0 9px
        }
        &.install {
          background-color: #000;
          border-radius: 0 9px 9px 0;
        }
      }
    }
  }
}
</style>