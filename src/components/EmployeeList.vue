<template>
  <div class="EmployeeList">
    <div class="container">
    <h1>Employees List</h1>      

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
          <tr v-bind:key="employe.id" v-for="employe in employee">
            <td>   <router-link :to="{path: `/SingleWorker?id=${employe.id}`}">{{employe.id}}</router-link></td>
            <td>{{employe.employee_name}}</td>
            <td>{{employe.employee_age}}</td>
            <td>{{employe.employee_salary}}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "EmployeeList",
  // props: ["employees"],
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
      axios
        .get("http://dummy.restapiexample.com/api/v1/employees")
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
</style>
