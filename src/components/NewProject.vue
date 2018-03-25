<template>
  <div class="container">
    <h4>New Project</h4>
    <div class="row">
      <form @submit.prevent="saveProject" class="col s12">
        <div class="row">
          <div class="input-field col s2">
            <input type="text" v-model="jobNumber" required>
            <label>Project #</label>
          </div>
          <div class="input-field col s2">
            <input type="text" v-model="customer" required>
            <label>Customer</label>
          </div>
          <div class="input-field col s8">
            <input type="text" v-model="description" required>
            <label>Description</label>
          </div>
        </div>
        <div class="row">
          <div class="input-field col s3">
            <input type="text" v-model="eng" required>
            <label>Designer</label>
          </div>
          <div class="input-field col s3">
            <input type="text" v-model="mech" required>
            <label>Technician</label>
          </div>
          <div class="input-field col s3">
            <input type="text" class="datepicker" v-model="shipDate" required>
            <label>Ship Date</label>
          </div>
          <div class="input-field col s3">
            <input type="text" v-model="status" required>
            <label>Status</label>
          </div> 
        </div>
        <button type="submit" class="btn blue-grey darken-2">Create New Project</button>
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
        shipDate: null
      }
    },
    methods: {
      saveProject () {
        db.collection('jobs').add({
          jobNumber: this.jobNumber,
          customer: this.customer,
          description: this.description,
          status: this.status,
          eng: this.eng,
          mech: this.mech,
          shipDate: this.shipDate
        })
        .then(docRef => {
          console.log('Project added: ', docRef.id)
          this.$router.push('/')
        })
        .catch(error => {
          console.error('Error adding project: ', error)
        })
      },
      datePickerInit () {
        $(document).ready(function(){
          $('.datepicker').datepicker();
        });
      }
    },
    beforeMount() {
      this.datePickerInit()
    }
  }
</script>
