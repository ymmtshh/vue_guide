<script setup lang="ts">
  import { ref, defineEmits } from 'vue'

  const inputtingDescription = ref<string>('')

  const emit = defineEmits(['post-tweet'])
  const postTweet = () => {
    emit('post-tweet', inputtingDescription.value )
  }

</script>

<template>
  <div class="form-container">
    <input v-model="inputtingDescription" />
    <button class="save-button" @click="postTweet()">post</button>
  </div>
</template>


<style scoped>
.form-container {
  align-items: center;
  background-color: aliceblue;
  border-radius: 4px;
  display: flex;
  flex-direction: column;
  margin-bottom: 12px;
  padding: 24px 0;
  width: 60%;
}

.save-button  {
  background-color:rgb(131, 152, 209);
  border: none;
  border-radius: 4px;
  color: #fff;
  font-weight: bold;
  height: 30px;
  margin-top: 12px;
  width: 120px;
}

.save-button:hover {
  background-color: #37dbdb;
}

</style>