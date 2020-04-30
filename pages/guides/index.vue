<template lang="pug">
  Default(:showNavbar="true")
    h1 Guides

    .guides
      nuxt-link(
        v-for="eachGuide in guides" v-bind:key="eachGuide.key"
        :to="'/guides/' + eachGuide.slug" 
      ).each-guide
        h2 {{ eachGuide.attr.title }}
        .excerpt {{ eachGuide.attr.excerpt }}
</template>

<script>
import Default from '~/layouts/Default.vue';
export default {
  head() {
    return {
      title: 'Guides',
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: `Learn how to make the most use of the NextBus SG mobile app - ${this.siteConfig}`
        }
      ]
    }
  },
  components: {
    Default,
  },
  asyncData ({ params, app }) {
    let guides = [];
    app.siteConfig.guides.forEach(async slug => {
      const mdFileContent = await import(`~/content/guides/${slug}.md`);
      guides.push({
        slug: slug,

        // includes title, description, excerpt, tags
        attr: mdFileContent.attributes
      });
    });

    return {
      guides
    };
  }
}
</script>

<style lang="scss" scoped>
.guides {

  .each-guide {
    display: block;

    // reset from <a> because nuxt-link used
    color: unset;
    text-decoration: unset;

    padding: var(--main-padding);
    background-color: var(--container-color);
    border-radius: var(--border-radius);

    border: 2px solid var(--border-color);

    h2 { margin: 0 }

    &:hover {
      background-color: var(--container-color-hover);
    }
  }

  .each-guide + .each-guide {
    margin-top: var(--main-padding);
  }
}
</style>