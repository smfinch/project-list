<template>
  <div class="container">
    <h4>New Project</h4>
    <div class="row">
      <form @submit.prevent="saveProject" class="col s12">
        <div class="row">
          <div class="input-field col s1">
            <input type="text" v-model="jobNumber" required>
            <label>Project #</label>
          </div>
          <div class="input-field col s2">
            <input type="text" v-model="customer" required>
            <label>Customer</label>
          </div>
          <div class="input-field col s9">
            <input type="text" v-model="description" required>
            <label>Description</label>
          </div>
        </div>
        <button type="submit" class="btn">Create New Project</button>
        <router-link to="/" class="btn grey right">Cancel</router-link>
      </form>
    </div>
  </div>
</template>

<script>
  import db from '@/config/firebaseInit'
  
  export default {
    name: 'newProject',
    data () {
      return {
        customer: null,
        description: null,
        jobNumber: null,
        eng: null,
        mech: null,
        status: null,
        location: {
          city: null,
          state: null,
        },
        shipDate: null
      }
    },
    methods: {
      saveProject () {
        db.collection('jobs').add({
          jobNumber: this.jobNumber,
          customer: this.customer,
          description: this.description
        })
        .then(docRef => {
          console.log('Project added: ', docRef.Id)
          this.$router.push('/')
        })
        .catch(error => {
          console.error('Error adding project: ', error)
        })
      }
    }
  }
</script>
