<template>
  <div id="app" class="small-container">
    <h1>Employees</h1>

    <employee-form @add:employee="addEmployee" />
    <employee-table v-bind:employees="employees" @delete:employee="deleteEmployee" />
  </div>
</template>

<script>
import EmployeeTable from './components/EmployeeTable'
import EmployeeForm from './components/EmployeeForm'

export default {
  name: 'App',
  components: {
    EmployeeTable,
    EmployeeForm,
  },
  data() {
    return {
      employees: [
        {
          id: 1,
          name: 'Bias Damiasa',
          email: 'biasd30@gmail.com'
        },
        {
          id: 2,
          name: 'Stephanie H. Unger',
          email: 'stephanie@jourrapide.com'
        },
        {
          id: 3,
          name: 'James T. McGinnis',
          email: 'james@armyspy.com'
        },
        {
          id: 4,
          name: 'Sashi Kirana',
          email: 'sashi@gmail.com'
        },
      ]
    }
  },
  methods: {
    addEmployee(emp) {
      const lastId = 
            this.employees.length > 0 ? 
                this.employees[this.employees.length-1].id : 0;
      const id = lastId + 1;
      const newEmployee = {...emp, id};
      this.employees = [...this.employees, newEmployee];
    },
    deleteEmployee(id) {
      this.employees = this.employees.filter(
        employee => employee.id !== id
      )
    }

  }
}
</script>

<style>
  button {
    background: #009435;
    border: 1px solid #009435;
  }

  .email-container {
    max-width: 680px;
  }
</style>
