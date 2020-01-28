<template>
    <nav class="navbar navbar-expand-lg navbar-light bg-light">
        <div class="container">
          <a href="#" class="navbar-brand">Star Wars <small class="text-secondary">Nuxt Optimized</small></a>
          <div id="navbarSupportedContent" class="collapse navbar-collapse">
            <ul class="navbar-nav mr-auto">
              <li class="nav-item active">
                <!-- <a href="#" class="nav-link">Home
                  <span class="sr-only">(current)</span>
                </a> -->
                <router-link to="/" class="nav-link">Home</router-link>
              </li> 
              <li class="nav-item">
                <a href="#" class="nav-link" role="button">Login</a>
              </li>
            </ul> 
            <form class="form-inline my-2 my-lg-0">
              <input type="search" placeholder="Search" aria-label="Search" class="form-control mr-sm-2"> <button type="submit" class="btn btn-outline-success my-2 my-sm-0">Search</button>
            </form>
          </div>
        </div>
    </nav>
    
</template>

<script>
export default {
  name: 'Header',
}
</script>

<style scoped>

</style>
