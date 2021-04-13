<template>
  <div class="Subscription">
    <Navbar />
    <div class="subscription__content">
      <v-container>
        
        <v-row  justify="center" no-gutters>
          
          <form> 
            <h5 style="color: #00506B;">Enter your phone number to continue</h5><br />
            <label for="email"><b>Phone Number</b></label>
            <input
              type="text"
              placeholder="eg: 0810242546724"
              name="email"
              id="email"
              required
            />
            <button type="submit" class="registerbtn">Register</button>
          </form>
        </v-row>
        <!-- <v-spacer></v-spacer> -->
        <!-- <p class="my-15 text-center" style="font-size: 12px">Copyright  © 2021. Class54 Education LTD.</p> -->
      </v-container>
       <Footer />
    </div>
   
  </div>
</template>
<script>
import Navbar from "@/components/Navbar";
import Footer from "@/components/Footer"
export default {
  name: "Subscription",
  components: {
    Navbar,
    Footer
  },
};
</script>

<style>

/* Full-width input fields */
input[type="text"] {
  width: 100%;
  padding: 10px;
  margin: 5px 0 22px 0;
  display: inline-block;
  border: none;
  background: #f1f1f1;
}

input[type="text"]:focus {
  background-color: #ddd;
  outline: none;
}

/* Set a style for the submit button */
.registerbtn {
  padding: 10px 12px;
  color: #fff;
  border: none;
  cursor: pointer;
  width: 100%;
  background: #29cc7a;
  border-radius: 4px;
}

.registerbtn:hover {
  opacity: 1;
}

form {
  margin-top: 100px;
}
.subscription__content {
  height: 92vh;
  background-color: #F4FAF6;
}
@media (max-width: 600px) {
    .subscription__content {
      height: 100vh;
    }
}
</style>
