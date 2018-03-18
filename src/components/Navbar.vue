<template>
  <nav>
    <div class="nav-wrapper blue-grey darken-3">
      <div class="container">
        <router-link to="/" class="brand-logo">Project List</router-link>
        <ul id="nav-mobile" class="right hide-on-med-and-down">
          <li><router-link to="/about">About</router-link></li>
        </ul>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  name: 'navbar'
}
</script>

