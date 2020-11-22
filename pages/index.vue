<template>
  <div>
    <div v-for="content in contents" :key="content.id">
      <nuxt-link :to="`/${content.id}`">
        <div>
          <img :src="content.image.url" alt="">
        </div>
        <div>
          {{ content.title }}          
        </div>
      </nuxt-link>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  async asyncData({$config}) {
    const { data } = await axios.get(
      process.env.baseUrl + '/api/v1/news',
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
