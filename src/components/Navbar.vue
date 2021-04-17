<template>
  <div class="nav">
    <v-container>
      <b-navbar toggleable="lg" type="light" variant="faded">
        <router-link to="/" exact tag="li">
       <a><img src="../assets/Logo.png" alt="Logo" class="nav-logo" /></a>
        </router-link>

        <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>
        <b-collapse id="nav-collapse" is-nav>
          <!-- Right aligned nav items -->
          <b-navbar-nav class="ml-auto" right>
            <div class="link-group">
              <router-link to="/download-page" exact tag="li"><a>Download app</a></router-link>
              <router-link to="/activate-page" exact tag="li"><a>Activate app</a></router-link>
            </div>
          </b-navbar-nav>
        </b-collapse>
      </b-navbar>
      <router-view></router-view>
    </v-container>
  </div>
</template>

<script>
export default {};
</script>

<style>
.nav-logo {
  width: 120px;
}
.v-application a {
  text-decoration: none !important;
  /* color: #696969 !important; */
  color: inherit;
  padding: 0 15px;
}
.navbar-light .navbar-toggler {
  border: none !important;
}

.router-link-exact-active {
  color: #00AE56 !important;
}

.link-group {
  display: flex;
}

@media (max-width: 600px) {
.v-application a {
padding: 0px 20px;
margin-top: 24px !important;
}
.footer {
    margin-top: 263px !important;
}
.link-group {
    margin-top: 47px;
    padding: 0 22px;
}
.nav .container {
   box-shadow: 0 8px 6px -6px #ccc;
}
}

@media (min-width: 1200px) {
  .container,
  .container-sm,
  .container-md,
  .container-lg,
  .container-xl {
    max-width: 1343px;
  }
}
</style>
