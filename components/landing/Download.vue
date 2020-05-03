<template lang="pug">
  .download
    h2(id="download") {{ download.title }}

    .store-buttons

      a(:href="download.ios.url" target="_blank")
        img(:src="require(`~/assets/images/${download.ios.image}`)")
      a(:href="download.android.url" target="_blank").android
        img(:src="require(`~/assets/images/${download.android.image}`)")
      //- a(href="") App Store
</template>

<script>
export default {
  props: ['download']
}
</script>

<style lang="scss" scoped>
.download {
  .store-buttons {
    display: flex;

    a {
      display: block;

      &.android {
        margin-left: var(--main-padding);
      }
      
      img {
        height: 3.5em;

        @include mobile-screen {
          height: 3em;
        }
      }
    }
  }
}
</style>