<template>
  <div class ='formObj'>
    <div class ='form-container'>
    <h1>Student Entry Form</h1>
    <form @submit.prevent="addStudent">
      <label>
        Name:
        <input v-model="form.name" required />
      </label>
      <br />
      <label>
        Reg:
        <input v-model="form.reg" required />
      </label>
      <br />
      <label>
        Marks:
        <input v-model.number="form.marks" type="number" required />
      </label>
      <button type="submit">Submit </button>
      <br />
    </form>

  </div>
  </div>
  <Listview 
  :students="students" 
  v-on:deleteitem="deleteItem"
  />
</template>
<script>
import Listview from '../components/List.vue'
export default {
  data() {
    return {
      form: {
        name: '',
        reg: '',
        marks: null,
      },
      students: [],
    }
  },
  methods: {
  addStudent() {
    this.students.push({ ...this.form })
    this.form.name = ''
    this.form.reg = ''
    this.form.marks = null
  },
  deleteItem(reg) {
    const pos = this.students.findIndex(s => s.reg === reg)
    if (pos === -1) {
      console.log('No Student found')
    } else {
      this.students.splice(pos, 1)
    }
  }
},
  components:{
    Listview,
  },
  }
</script>

<style lang="css">
#student-list table {
  width: 100%;
  border-collapse: collapse;
  color: #f0f0f0;
  font-size: 0.95rem;
}

#student-list th,
#student-list td {
  border: 1px solid #444;
  padding: 0.75rem;
  text-align: left;
}

#student-list th {
  background-color: #3a3a3a;
}

#student-list tr:nth-child(even) {
  background-color: #2e2e2e;
}

#student-list tr:nth-child(odd) {
  background-color: #383838;
}

.form-container {
  width: 100%;
  max-width: 400px;
  background-color: #2b2b2b;
  padding: 2rem;
  border-radius: 10px;
  
}

.form-container h1 {
  margin-bottom: 1.5rem;
  font-size: 1.5rem;
  text-align: center;
}

.form-container label {
  display: block;
  margin-bottom: 1rem;
  font-weight: 500;
}

.form-container input {
  width: 100%;
  padding: 0.6rem 0.8rem;
  margin-top: 0.25rem;
  border: 1px solid #555;
  border-radius: 6px;
  background-color: #3a3a3a;
  color: #fff;
  font-size: 1rem;
}

.form-container input:focus {
  outline: none;
  border-color: #00bcd4;
  background-color: #444;
}

.form-container button {
  margin-top: 1rem;
  padding: 0.7rem 1.2rem;
  border: none;
  background-color: #00bcd4;
  color: white;
  font-weight: bold;
  border-radius: 6px;
  cursor: pointer;
  width: 100%;
  transition: background-color 0.2s ease;
}

.form-container button:hover {
  background-color: #0097a7;
}
</style>