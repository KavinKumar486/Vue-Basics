<template>
    <div id="student-list">
  <h2>Student List</h2>
  <table>
    <thead>
      <tr>
        <th>No</th>
        <th>Name</th>
        <th>Reg</th>
        <th>Marks</th>
        <th>Options</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="(student, index) in students" :key="index">
        <td>{{ index + 1 }}</td>
        <td>{{ student.name }}</td>
        <td>{{ student.reg }}</td>
        <td>{{ student.marks }}</td>
        <td><input @click="$emit('deleteitem',student.reg)" type="Submit" value="Delete"></td>
      </tr>
    </tbody>
  </table>
</div>
</template>
<script setup>
const props = defineProps({
  students:{
    type:Array,
    required:true
  }
  
})
</script>