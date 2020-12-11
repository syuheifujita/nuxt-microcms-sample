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
      process.env.baseUrl + '/api/v1/blog',
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
