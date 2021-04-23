<template>
  <div class="Subscription">
    <Navbar />
    <div class="subscription__content">
      <v-container>
        <v-row justify="center" no-gutters>
          <form>
            <h5 style="color: #00506B;">Enter your phone number to continue</h5>
            <br />
            <label for="number"><b>Phone Number</b></label>
            <input
              type="text"
              placeholder="eg: 0810242546724"
              name="number"
              id="number"
              v-model="email"
              required
            />
            <!-- <button type="submit" class="registerbtn">Proceed</button> -->
            <paystack
              :amount="200000"
              :email="email"
              :paystackkey="paystackkey"
              :reference="reference"
              :callback="callback"
              :close="close"
              :embed="false"
              class="btn subscriptionbtn w-100 mt-5"
            >
              Proceed
            </paystack>
          </form>
        </v-row>
        <!-- <v-spacer></v-spacer> -->
        <!-- <p class="my-15 text-center" style="font-size: 12px">Copyright  © 2021. Class54 Education LTD.</p> -->
      </v-container>
      <Footer class="sub-footer"/>
    </div>
  </div>
</template>
<script>
import Navbar from "@/components/Navbar";
import Footer from "@/components/Footer";
import paystack from "vue-paystack";
export default {
  name: "Subscription",
  components: {
    Navbar,
    Footer,
    paystack,
  },
  data() {
    return {
      paystackkey: "pk_test_7ec5ca2a828fc887b0a394b93a6d814725d7c0e5", //paystack public key
      formData: {
        email: this.formData.email, // Customer email
        amount: 0, // in kobo
      },
    };
  },
  computed: {
    reference() {
      let text = "";
      let possible =
        "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789";

      for (let i = 0; i < 10; i++)
        text += possible.charAt(Math.floor(Math.random() * possible.length));

      return text;
    },
  },
  methods: {
    callback: function(response) {
       if (response.status == "success") {
        const ref = response.trxref;
        this.response({ ref });
      } else {
        alert("Something went wrong! Please try again");
      }
    },
    close: function() {
      console.log("Payment closed");
    },
    postData(e) {
      this.axios
        .post("https://api.paystack.co/transaction/initialize", this.formData)
        .then((result) => {
          console.log(result);
        });
      this.formData = "";
      e.preventDefault();
    },
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
  background: #fff;
}

input[type="text"]:focus {
  background-color: #ddd;
  outline: none;
  transition: background-color 0.5s ease;
}
  .sub-footer {
    padding-top: 19%;
  }
::-webkit-input-placeholder {
  color: #bdbdbd;
} /* Chrome/Opera/Safari */
::-moz-placeholder {
  color: #bdbdbd;
} /* Firefox 19+ */
:-ms-input-placeholder {
  color: #bdbdbd;
} /* IE 10+ */
:-moz-placeholder {
  color: #bdbdbd;
}

/* Set a style for the submit button */
.subscriptionbtn {
  padding: 10px 12px;
  color: #fff !important;
  border: none;
  cursor: pointer;
  width: 100%;
  background: #29cc7a;
  border-radius: 4px;
}

.subscriptionbtn:hover {
  opacity: 1;
}

form {
  margin-top: 150px;
}
form h5 {
  font-weight: 700;
  font-size: 16px;
}
.subscription__content {
  height: 100vh;
  background-color: #f4faf6;
  padding-top: 2%;
}
@media (max-width: 600px) {
  .subscription__content {
    height: 100vh;
  }
  .sub-footer {
    padding-top: 65%;
  }
}
</style>
