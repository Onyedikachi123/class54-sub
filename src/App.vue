<template>
  <v-app>

    <v-main> 
      <router-view></router-view>
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
}
main {
  background: linear-gradient(180deg, #e3fff1 -82.57%, #ffffff 100%);
  font-family: 'Source Sans Pro', sans-serif;
}

</style>