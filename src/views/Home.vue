<template>
  <div class="home">
    <Dashboard />
    <div class="fixed-action-btn">
      <router-link to="/new" class="btn-floating btn-large waves-effect waves-light red"><i class="material-icons">add</i></router-link>
    </div>
  </div>
</template>

<script>

import Dashboard from '@/components/Dashboard.vue'

export default {
  name: 'home',
  components: {
    Dashboard,
  }
}
</script>
