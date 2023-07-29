<script setup lang="ts">
  import { defineProps } from 'vue';
  type Tweet = {
    id: number,
    description: string
  }

  type Props = {
    tweets: Tweet[]
  }

  const deleteTweet = (id: number) => {
    console.log('delete')
  }

  defineProps<Props>()
  </script>

<template>
  <li v-for="tweet in tweets" :key="tweet.id" class="tweet-list">
    <span>{{ tweet.description }}</span>
    <button class="delete-button" @click="deleteTweet(tweet.id)">delete</button>
  </li>
</template>

<style scoped>

.tweet-list {
  list-style: none;
  margin: 0 0 12px 0;
  border-radius: 4px;
  font-size: 12px;
  display: flex;
  justify-content: space-between;
  background-color: rgb(186, 210, 231);
  padding: 8px 20px;
  width: 300px;
}

.delete-button  {
  color: #fff;
  font-weight: bold;
  background-color: #c99a68;
  border-radius: 4px;
  border: none;
  width: 120px;
  height: 30px;
}

.delete-button:hover {
  background-color: rgb(255, 132, 0);
}

</style>