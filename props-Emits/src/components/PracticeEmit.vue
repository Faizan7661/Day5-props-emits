<script setup>
const props = defineProps({
    employeeDetails:{
        type :Object,
        required : true
    }

})

const emit = defineEmits(['editNumber'])

const editNumber =()=>{
    emit('editNumber', props.employeeDetails.id)
}
</script>

<template>
    <div>
       
        <div><h3>{{ employeeDetails.employeeName }}</h3></div>
        <div><h3>{{ employeeDetails.designation }}</h3></div>
        <div><h3>{{ employeeDetails.mobileNumber }}</h3></div>
        <div><button @click="editNumber">Edit Employee number</button></div>
        <br>
        <hr>

    </div>
</template>