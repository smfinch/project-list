<template>
  <div class="container">
    <h4>New Project</h4>
    <div class="row">
      <form class="col s12">
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
      </form>
    </div>
  </div>
</template>

<script>
  import db from '../config/firebaseInit'
  
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

      }
    }
  }
</script>
