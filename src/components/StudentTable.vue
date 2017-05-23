<script>
import axios from 'axios';
import StudentLine from './StudentLine';
import addStudent from './addStudent';

export default {
  components: {
    addStudent,
    StudentLine,
  },
  data() {
    return {
      students: [],
    };
  },
  methods: {
    getAll() {
      axios.get('http://localhost:3000/students')
        .then((response) => {
          this.students = response.data;
        });
    },
    addOne(a) {
      const newStudent = { firstname: a };
      axios.post('http://localhost:3000/students', newStudent)
        .then((res) => {
          this.students.push(res.data);
        });
    },
    remove(index) {
      axios.delete(`http://localhost:3000/students/${this.students[index].id}`)
        .then(() => {
          this.students.splice(index, 1);
        });
    },
  },
  mounted() {
    this.getAll();
  },
};
</script>

<template>
<div>
  <student-line v-for='(student, index) in students' :student="student" v-on:remove="remove(index)"> </student-line>
  <add-student v-on:addOne="addOne"></add-student>
</div>
</template>

<style>

</style>
