<script setup>
import { ref } from "vue";
import SinglePost from "./SinglePost.vue";
import PracticeEmit from "./PracticeEmit.vue"
let posts = ref([
  { id: 1, title: "Post 1" },
  { id: 2, title: "Post 2" },
  { id: 3, title: "Post 3" },
]);
const updatePost = (postId) => {
  posts.value = posts.value.map((post) => {
    if (post.id === postId)
      return { ...post, title: "Updated Title Using Props and Emit" };
    return post;
  });
};

//practiceEmits component logic and data

let employeeDetails = ref([
  {
    id: 48,
    employeeName: "Mohammed Faizan",
    designation: "Software Engineer",
    mobileNumber: 1234567890,
  },
  {
    id: 49,
    employeeName: "Nikhil",
    designation: "Software Engineer",
    mobileNumber: 1234567890,
  },
  {
    id: 50,
    employeeName: "Tarun",
    designation: "Software Engineer",
    mobileNumber: 1234567890,
  },
  {
    id: 51,
    employeeName: "Zaid",
    designation: "Software Engineer",
    mobileNumber: 1234567890,
  },
]);

const updateEmpNum = (employeeId) => {
  employeeDetails.value = employeeDetails.value.map((employee) => {
    if (employee.id === employeeId) {
      return { ...employee, mobileNumber: "0987654321" };
    }
    return employee;
  });
};

</script>

<template>
  <div>
    <h3>Post Details :</h3>
    <hr />
    <SinglePost
      v-for="post in posts"
      :post="post"
      :key="post.id"
      @edit-post="updatePost"
    />
    <h1> Implementation of learning props and emits</h1>

    <PracticeEmit
      v-for="employee in employeeDetails"
      :key="employee.id"
      :employeeDetails="employee"
      @edit-number ="updateEmpNum"
    />

  </div>
</template>
