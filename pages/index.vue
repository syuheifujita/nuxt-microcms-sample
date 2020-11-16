<template>
  <ul>
    <li v-for="content in contents" :key="content.id">
      <nuxt-link :to="`/${content.id}`">
        {{ content.title }}
      </nuxt-link>
    </li>
  </ul>
</template>

<script>
import axios from 'axios';

export default {
  async asyncData({$config}) {
    const { data } = await axios.get(
      'https://nuxt-sample.microcms.io/api/v1/news',
      {
        headers: { 
          'X-API-KEY': $config.apiKey
          // 'X-API-KEY': 'ef7399c4-fd48-46d2-92d9-634226fbd754'
        }
      }
    )
    return data
  }
}
</script>
