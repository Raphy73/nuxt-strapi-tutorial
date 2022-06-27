<template>
  <div>
    <div class="bg-white">
      <div class="max-w-2xl mx-auto py-24 px-4 sm:py-8 sm:px-6 lg:max-w-7xl lg:px-8">
        <div class="mt-11 grid items-start grid-cols-1 gap-y-16 gap-x-6 sm:mt-16 sm:grid-cols-2 lg:grid-cols-4 lg:gap-x-8">
          <Article v-for="article in articles.data" :key="article.id" :id="article.id" :title="article.attributes.title" :image="article.attributes.image.data.attributes.formats.thumbnail.url" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'IndexPage',
  data() {
    return {
      articles: [],
    }
  },
  async mounted () {
    try {
      this.articles = await this.$strapi.$articles.find({populate: '*'});
    } catch (error) {
      this.error = error
    }
    console.log(this.articles);
  }
}
</script>
