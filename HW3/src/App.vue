<template>
  <div>
    <div v-for="post in posts" :key="post.id">
      <label :for="'color-' + post.id">Text color</label>
      <input type="text" :id="'color-' + post.id" v-model="post.color" /><br />
      <label :for="'background-' + post.id">background color</label>
      <input type="text" :id="'background-' + post.id" v-model="post.background" /><br />
      <label :for="'font_size-' + post.id">font size</label>
      <input type="text" :id="'font_size-' + post.id" v-model="post.fontSize" /><br />
      <div :style="getStyle(post)">
        
        <p>{{ post.content }}</p>
      </div>
      
      <label :for="'redact-' + post.id">Edit</label>
      <textarea :id="'redact-' + post.id" cols="30" rows="3" v-model="post.newText" @input="setText(post.id, post.newText)"></textarea>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
const posts = ref([
  {
    id: '1',
    title: 'title1',
    content: 'content1',
    color: 'black', 
  },
  {
    id: '2',
    title: 'title2',
    content: 'content2',
    color: 'black', 
  },
  {
    id: '3',
    title: 'title3',
    content: 'content3',
    color: 'black', 
  },

])  

function setText(id, newText){
  for(let post of posts.value){
    if(post.id == id){
      post.content = newText
    }
  }
}


function getStyle(post) {
  return {
    color: post.color,
    background: post.background,
    fontSize: post.fontSize,
    fontFamily: post.fontFamily,
    fontStyle: post.fontStyle
  };
}
</script>

<style scoped>

</style>