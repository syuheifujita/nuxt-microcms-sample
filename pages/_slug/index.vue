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
  async asyncData({ $config, params }) {
    const { data } = await axios.get(
      process.env.baseUrl + '/api/v1/blog/' + params.slug,
      {
        headers: { 
          'X-API-KEY': $config.apiKey
        }
      }
    )
    return data
  }
}
</script>
