<template>
  <div>
    <div class="flex flex-col-reverse">
        <div class="mt-6">
            <h3 class="text-sm font-medium text-gray-900 mb-4">{{ title }}</h3>
            <nuxt-link :to="{ name: 'article-id', params: { id: id } }" class="text-sm bg-purple-900 text-white p-2 rounded">Read article</nuxt-link>
        </div>
        <div class="aspect-w-1 aspect-h-1 rounded-lg bg-gray-100 overflow-hidden">
            <img :src="'http://localhost:1337' + image" alt="Green cardstock box containing white, beige, and brown cards." class="object-center object-cover w-full">
        </div>
    </div>
    {{ theGoodArticle }}
  </div>
</template>

<script>
export default {
  props: ["title", "id", "image"],
}
</script>

<style>

</style>