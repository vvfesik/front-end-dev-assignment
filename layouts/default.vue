<template>
  <div>
    <h1 class="display-4 mt-5 text-center">{{ seo.description }}</h1>
    <nuxt />
  </div>
</template>

<script>
export default {
  data() {
    return {
      seo: {
        title: 'Best car wash in Texas',
        description: 'Probably the best car wash in Texas',
        siteName: 'Best Texas car wash',
        image: '~assets/img/best-texas-car-wash-1200x630.png',
        url: 'https://front-end-dev-assignment.firebaseapp.com',
        twitterName: '@basil2k'
      }
    };
  },
  head() {
    return {
      title: this.seo.title,
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: this.seo.description
        },
        {
          hid: 'og:title',
          property: 'og:title',
          content: this.seo.title
        },
        {
          hid: 'og:description',
          property: 'og:description',
          content: this.seo.description
        },
        {
          hid: 'og:image',
          property: 'og:image', 
          content: this.seo.image
        },
        {
          hid: 'og:url',
          property: 'og:url',
          content: this.seo.url
        },
        {
          hid: 'twitter:card',
          name: 'twitter:card',
          content: 'summary_large_image'
        },
        {
          hid: 'og:site_name',
          property: 'og:site_name',
          content: this.seo.siteName
        },
        {
          hid: 'twitter:image:alt',
          name: 'twitter:image:alt',
          content: this.seo.title
        },
        {
          hid: 'twitter:site',
          name: 'twitter:site',
          content: this.seo.twitterName
        }
      ]
    };
  }
};
</script>

<style>
</style>
