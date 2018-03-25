<template>
  <div class="container">
    <h4>Dashboard</h4>
    <table class="highlight">
      <thead>
        <tr>
          <th>Job Number</th>
          <th>Customer</th>
          <th>Description</th>
          <th>Status</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="project in projects" :key="project.id">
          <td>{{project.jobNumber}}</td>
          <td>{{project.customer}}</td>
          <td>{{project.description}}</td>
          <td>{{project.status}}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
  import db from '../config/firebaseInit'
  export default {
    name: 'dashboard',
    data () {
      return {
        projects: []
      }
    },
    created () {
      db.collection('jobs').get().then((querySnapshot) => {
        querySnapshot.forEach((doc) => {
          const data = {
            'id': doc.id,
            'customer': doc.data().customer,
            'description': doc.data().description,
            'jobNumber': doc.data().jobNumber,
            'eng': doc.data().eng,
            'mech': doc.data().mech,
            'status': doc.data().status,
            'shipDate': doc.data().shipDate,
          }
          this.projects.push(data)
        })
      })
    }
  }
</script>
