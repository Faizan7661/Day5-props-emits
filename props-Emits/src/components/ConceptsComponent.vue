<script setup>
// This is an example of declaring props using array
// const props = defineProps(['title'])

// This is the example of declaring props using object which helps in type validation

const props = defineProps({
  title: {
    type : String,
    required : true,
    default : "This is a title from default"
  },
  
  id:Number,
  date :String
});


</script>

<template>
  <div>
    <h1 class="title">
      {{ props.title }}
      {{ props.id }}
      {{ props.date }}
    </h1>
  </div>
</template>

<style scoped>
.title {
  text-align: center;
}
</style>
