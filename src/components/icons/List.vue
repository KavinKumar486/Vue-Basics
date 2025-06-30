<template>
    <div id="student-list">
  <h2>Student List</h2>
  <table>
    <thead>
      <tr>
        <th>#</th>
        <th>Name</th>
        <th>Reg</th>
        <th>Marks</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="(student, index) in students" :key="index">
        <td>{{ index + 1 }}</td>
        <td>{{ student.name }}</td>
        <td>{{ student.reg }}</td>
        <td>{{ student.marks }}</td>
      </tr>
    </tbody>
  </table>
</div>
</template>
<script setup>
const props = defineProps({
  students: Array
})
</script>