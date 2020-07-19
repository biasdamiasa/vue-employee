<template>

    <div id="employee-table">
        <p v-if="employees.length < 1" class="empty-table">
            No employees
        </p>
        <table v-else>
            <thead>
                <tr>
                    <th>Name</th>
                    <th>Email </th>
                    <th>Actions</th>
                </tr>
            </thead>
            <tbody>
        <tr v-for="employee in employees" :key="employee.id">
          <td>{{ employee.name }}</td>
          <td>{{ employee.email }}</td>
          <td>
              <button>Edit</button>
              <button @click="$emit('delete:employee', employee.id)">Delete</button>
          </td>
        </tr>
      </tbody>
        </table>
    </div>

</template>

<style scoped>
    button {
        margin: 0 0.5rem 0 0;
    }
</style>

<script>
export default {
 name: 'employee-table',
 props: {
     employees: Array
 },
}
</script>