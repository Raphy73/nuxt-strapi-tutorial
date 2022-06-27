<template>
  <div>
        <div class="bg-white">
            <section aria-labelledby="features-heading" class="max-w-7xl mx-auto py-28 sm:px-2 lg:px-8">
            <div class="max-w-2xl mx-auto px-4 lg:px-0 lg:max-w-none">
                <div class="max-w-3xl">
                <h2 id="features-heading" class="text-3xl font-extrabold tracking-tight text-gray-900 sm:text-4xl">{{ theArticle.title }}</h2>
                </div>
                <div class="mt-4">
                    <div id="features-panel-1" class="space-y-16 pt-10 lg:pt-16" aria-labelledby="features-tab-1" role="tabpanel" tabindex="0">
                        <div class="flex flex-col-reverse lg:grid lg:grid-cols-12 lg:gap-x-8">
                            <div class="mt-6 lg:mt-0 lg:col-span-12">
                                <p class="mt-2 text-sm text-gray-500">{{ theArticle.content }}</p>
                            </div>
                            <div>
                                <div class="aspect-w-2 aspect-h-1 rounded-lg bg-gray-100 overflow-hidden sm:aspect-w-5 sm:aspect-h-2">
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            </section>
        </div>
  </div>
</template>

<script>
export default {
    data() {
        return {
            articles: [],
            theArticle: [],
            id: this.$route.params.id,
            error: null,
        }
    },
    async mounted () {
        try {
            this.articles = await this.$strapi.$articles.find({populate: '*'});
            this.articles = this.articles.data;
            this.articles.forEach(element => {
                if(element.id == this.id) {
                    this.theArticle.push(element.attributes);
                    this.theArticle = this.theArticle[0];
                }
            });
        } catch (error) {
            this.error = error
        }
    } 
}
</script>

<style>

</style>