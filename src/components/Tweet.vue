<script setup lang="ts">
  import { ref } from 'vue'
  import TweetPostForm from './TweetPostForm.vue'
  import TweetList from './TweetList.vue'


  const tweets = ref([{id: 0, description: 'Hello World!'}, {id:1, description: 'this is the second tweet.'}])

  const inputtingDescription = ref<string>('')

  const postTweet = (description: string) => {
    const tweet = { id: Math.random(), description}
    tweets.value.push(tweet)
    console.log('post...', tweets.value)
  }

  const deleteTweet = (id: number) => {
    tweets.value = tweets.value.filter(t => t.id !== id)
  }

</script>

<template>
  <div class="container">
    <h1>Tweeter</h1>
    <TweetPostForm @post-tweet="postTweet"/>
    <div class="tweet-container">
      <p v-if="tweets.length <= 0">No tweets have been added</p>
      <ul>
        <TweetList :tweets="tweets" @delete-tweet="deleteTweet"/>
        <!-- <li v-for="tweet in tweets" :key="tweet.id" class="tweet-list">
          <span>{{ tweet.description }}</span>
          <button class="delete-button" @click="deleteTweet(tweet.id)">delete</button>
        </li> -->
      </ul>
    </div>
  </div>
</template>

<style scoped>


.container {
  display: flex;
  flex-direction: column;
  align-items: center;
}

</style>