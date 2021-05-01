<template>
  <div class="Loader">
    <Navbar />
    <div class="loader__content">
      <v-container>
        <v-row justify="center" no-gutters>
         <div>
          <SpinnerLoader :color="'#29CC7A'" style="margin-top: 350px;"/>
          <!-- <p>Kindly wait while we automatically activate your App </p> -->
          </div>
        </v-row>
      </v-container>
    </div>
  </div>
</template>

<script>
import { SpinnerLoader } from "vue-spinners-css";
import Navbar from "@/components/Navbar";


export default {
  name: "Loader",
  components: {
    SpinnerLoader,
    Navbar,
    
  },
};
</script>

<style>

.Loader .loader__content {
    height: 100vh;
  background-color: #f4faf6;
}
</style>
