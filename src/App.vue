<template>
  <v-app>
    <v-main> 
      <transition
      mode="out-in"
      enter-active-class="animate__animated animated__fadeIn"
      leave-active-class="animate__animated animated__fadeOut"
      >
      <router-view></router-view>
      </transition>
    </v-main>
  </v-app>
</template>

<script>


export default {
  name: 'App',

  data: () => ({
    //
  }),
};
</script>
<style>
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
main {
  font-family: 'Source Sans Pro', sans-serif;
}

</style>