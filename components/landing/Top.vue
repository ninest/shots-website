<template lang="pug">
  .top
    .right 
      .title 
        h1 {{ title }}
        .subtitle {{ subtitle }}

      .action
        nuxt-link(:to="action.main.url").main {{ action.main.text }}
        nuxt-link(:to="action.secondary.url").secondary {{ action.secondary.text }}
    
    .left
      img(:src="require(`~/assets/images/landing/${mainImage}`)")
</template>

<script>
export default {
  props: ['title', 'subtitle', 'action', 'mainImage']
}
</script>

<style lang="scss" scoped>
.top {
  margin-top: calc(var(--extra-padding) * 5);

  @include mobile-screen {
    maring-top: var(--dense-padding);
  }

  @include mobile-screen { margin-top: var(--main-padding); }

  display: grid;
  grid-template-columns: 3fr 1fr;
  grid-template-areas: "right left";
  grid-gap: var(--extra-padding);

  @include mobile-screen {
    grid-template-columns: 1fr;
    grid-template-areas: 
      "left"
      "right";
  }

  @include mobile-screen {
    // height: 89vh;
  }

  .right {
    
    @include not-mobile-screen{margin-top: 3.5em;}


    grid-area: right;
    .title {
      h1 {
        font-size: 3.8em;
        padding: 0; margin: 0;
      }
      .subtitle {
        font-size: 1.5em;
        font-weight: 400;
      }
      @include mobile-screen {
        h1 { font-size: 2.5em; }
        .subtitle { font-size: 1.3em }
      }

      margin-bottom: var(--extra-padding);

    }

    .action {
      display: flex;

      & a {
        display: block;
        padding: var(--main-padding) calc(var(--main-padding) * 3) ;
        @include mobile-screen {
          padding: var(--main-padding);
          width: 50%;
          text-align: center;
        }

        border-radius: var(--border-radius);
        text-decoration: unset;

        &.main {
          color: white;
          background-color: var(--accent-color);
        }
        &.secondary {
          margin-left: var(--main-padding);
          box-shadow: inset 0 0 0 3px var(--accent-color);
          // , inset 0 0 0 10px white;

          color: var(--accent-color);
        }
      }

    }
  }

  .left {
    grid-area: left;
    img {

      @include not-mobile-screen {
        height: 650px;
        margin-top: -80px;
      }

      @include mobile-screen {
        // height: 50vh;
        max-width: 100%;
        max-height: 60vh;

        width: auto;
        height: auto;

        // center
        display: block;
        margin: 0 auto;
      }

      border-radius: calc(var(--border-radius) * 2);
    }
  }


  margin-bottom: calc(var(--extra-padding) * 3);
}
</style>