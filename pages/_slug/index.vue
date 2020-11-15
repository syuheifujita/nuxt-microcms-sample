<template>
  <main class="main">
    <h1 class="title">{{ title }}</h1>
    <p class="publishedAt">{{ publishedAt }}</p>
    <div class="post" v-html="body"></div>
  </main>
</template>

<script>
import axios from 'axios'

export default {
  async asyncData({ params }) {
    const { data } = await axios.get(
      `https://nuxt-sample.microcms.io/api/v1/news/${params.slug}`,
      {
        headers: { 'X-API-KEY': 'ef7399c4-fd48-46d2-92d9-634226fbd754' }
      }
    )
    return data
  }
}
</script>
