<script setup lang="ts">
  import { ref } from 'vue'
  const tweets = ref([{id: 0, description: 'Hello World!'}, {id:1, description: 'this is the second tweet.'}])

  const inputtingDescription = ref<string>('')

  const postTweet = () => {
    const tweet = { id: Math.random(), description:inputtingDescription.value}
    tweets.value.push(tweet)
    inputtingDescription.value = ''
    console.log('post...', tweets.value)
  }

  const deleteTweet = (id: number) => {
    tweets.value = tweets.value.filter(t => t.id !== id)
  }

</script>

<template>
  <div class="container">
    <h1>Tweeter</h1>
    <div class="form-container">
      <input v-model="inputtingDescription" />
      <button class="save-button" @click="postTweet()">post</button>
    </div>
    <div class="tweet-container">
      <ul>
        <li v-for="tweet in tweets" :key="tweet.id" class="tweet-list">
          <span>{{ tweet.description }}</span>
          <button class="delete-button" @click="deleteTweet(tweet.id)">delete</button>
        </li>
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

.form-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: aliceblue;
  padding: 24px 0;
  width: 60%;
  margin-bottom: 12px;
  border-radius: 4px;
}

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

.save-button  {
  color: #fff;
  font-weight: bold;
  background-color:rgb(131, 152, 209);
  border-radius: 4px;
  border: none;
  width: 120px;
  height: 30px;
}

.save-button:hover {
  background-color: #37dbdb;
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



input {
  margin: 0 0 16px 0;
}

</style>