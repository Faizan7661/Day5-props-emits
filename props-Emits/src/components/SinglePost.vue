<script setup>
const props = defineProps({
  post: {
    type: Object,
    required: true,
  },
});
</script>

<template>
    <div>Id : {{ post.id }}</div>
    <div>Title : {{ post.title }}</div>
    <div><button @click.prevent="$emit('editPost', post.id)">Edit Post Title</button></div>
    <br>
    <hr>
  </template>