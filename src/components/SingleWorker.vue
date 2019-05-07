<template>
  <div class="SingleWorker">
    <div class="container">
      <h1>SingleWorker</h1>
     <router-link class="btn btn-primary" to="/">Back</router-link>
      <table class="table table-hover">
        <thead>
          <tr>
            <th>id</th>
            <th>name</th>
            <th>age</th>
            <th>salary</th>
          </tr>
        </thead>
        <tbody>
          <tr >
            <td>{{employee.id}}</td>
            <td>{{employee.employee_name}}</td>
            <td>{{employee.employee_age}}</td>
            <td>{{employee.employee_salary}}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "SingleWorker",
  data() {
    return {
      employee: []
    };
  },
  created: function() {
    this.getapi();
  },
  methods: {
    getapi() {
      const id = this.$route.query.id;
      axios
        .get(`http://dummy.restapiexample.com/api/v1/employee/${id}`)
        .then(res => {
          console.log(res.data), (this.employee = res.data);
        })
        .catch(arr => console.log(arr));
    }
  }
};
</script>

<style scoped>
.container {
  margin-top: 100px;
}
.container h1 {
  color: #3f43b5;
  text-align: center;
  margin-bottom: 25px;
}
a.btn.btn-primary{
    margin-bottom: 25px;
}
</style>
