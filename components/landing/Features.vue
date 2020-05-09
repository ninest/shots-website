<template lang="pug">
  .features
    h2(id="features") {{ features.title }}

    .list
      div(
        v-for="f in features.list" :key="f.text"
        :class="{'image-left': f.imageLeft}"
      ).each-feature 
        //- .graphic
        img(:src="require(`~/assets/images/landing/${f.image}`)" :class="{'image-left': f.imageLeft}")
        //- div(:class="{ className: data }")
        .text
          h3 {{ f.text }}
          .description {{ f.description }}
          a(v-if='f.button' :href="f.button.url") {{ f.button.text }}
</template>

<script>

export default {
  props: ['features']
}
</script>

<style lang="scss" scoped>
h2 {
  visibility: hidden;
}

.list {
  .each-feature {

    display: grid;
    grid-template-columns: 1fr min-content;
    grid-template-areas: "text image";
    grid-gap: var(--large-padding);

    // conditional to put image on left side
    &.image-left {
      grid-template-columns: min-content 1fr;
      grid-template-areas: "image text";
    }


    // different layout for mobile

    @include mobile-screen {
      &, &.image-left {
        grid-template-columns: 1fr;
        grid-template-areas: "text"
                             "image";
      }
    }

    img {
      grid-area: image;
      height: 70vh;

      // center image on mobile
      @include mobile-screen {
        height: 60vh;
        margin: 0 auto;
      }
    }

    .text {
      grid-area: text;

      // on desktop, center in vertically
      @include not-mobile-screen {
        margin: var(--large-padding);
      }

      h3 {
        font-size: 2.0em;
      }
      .description {
        font-size: 1.4em;
      }
    }


    margin-bottom: var(--large-padding);
  }
}
</style>