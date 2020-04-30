<template lang="pug">
  Root
    Navbar(v-if="showNavbar" :extendedWidth="extendedWidth")

    .wrapper
      main(:class="{ 'extended-width': extendedWidth }")
        slot

      Footer(:extendedWidth="extendedWidth")
</template>

<script>
import Root from '~/layouts/Root.vue';
import Navbar from '~/components/Navbar.vue';
import Footer from '~/components/Footer.vue';

export default {
  components: {
    Root, Navbar, Footer
  },
  props: {
    showNavbar: {
      default: true,
      required: false,
    },
    extendedWidth: {
      default: false,
      required: false,
    }
  }
}
</script>

<style lang="scss" scoped>

main {
  padding: var(--main-padding) var(--side-padding);
  padding-top: 0;


  &.extended-width {
    // background-color: red;
    
    @include desktop-screen { 
      // margin: 0 -10%; 
      padding: var(--main-padding) 10%;
    }
  }
}


</style>