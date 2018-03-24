<template>
  <div class="container">
    <h4>Dashboard</h4>
    <div class="collection">
      <a href="#" class="collection-item" v-for="project in projects" :key="project.id">{{project.jobNumber}}</a>
    </div>
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
            'location': doc.data().location,
            'shipDate': doc.data().shipDate,
          }
          this.projects.push(data)
        })
      })
    }
  }
</script>
