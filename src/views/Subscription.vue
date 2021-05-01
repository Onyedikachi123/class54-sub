<template>
  <div class="Subscription">
    <Navbar />
    <div class="subscription__content">
      <v-container>
        <v-row justify="center" no-gutters>
          <div class="form">
            <h5 style="color: #00506B;">Enter your phone number to continue</h5>
            <br />
            <label for="number"><b>Phone Number</b></label>
            <input
              type="tel"
              placeholder="eg: 080856789787"
              name="phone"
              id="phone"
              v-model="phone"
              
              required
            />
            <!-- <button type="submit" class="registerbtn">Proceed</button> -->
            <paystack
              :amount="amount * 100"
              :email="`${phone}@class54.com`"
              :paystackkey="paystackkey"
              :reference="reference"
              :callback="processPayment"
              :close="close"
              class="btn subscriptionbtn w-100 mt-5"
            >
              Proceed
            </paystack>
          </div>
        </v-row>
        <!-- <v-spacer></v-spacer> -->
        <!-- <p class="my-15 text-center" style="font-size: 12px">Copyright  © 2021. Class54 Education LTD.</p> -->
      </v-container>
      <Footer class="sub-footer" />
    </div>
  </div>
</template>
<script>
// import { mapGetters, mapActions } from "vuex";
import Navbar from "@/components/Navbar";
import Footer from "@/components/Footer";
import paystack from "vue-paystack";
import axios from "axios";
// import VueAxios from "vue-axios";
// Vue.use(VueAxios, axios);
export default {
  name: "Subscription",
  components: {
    Navbar,
    Footer,
    paystack,
  },
  data () {
    return {
      paystackkey: "pk_test_7ec5ca2a828fc887b0a394b93a6d814725d7c0e5",
      phone: "",
      transaction_ref: "",
      machineid: this.$route.query.machineid,
      serial: this.$route.query.serial,
      amount: 2000,
      Subscription: {},
      channels: ['card']
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
    processPayment(response)  {
      // console.log(response)
      this.transaction_ref = response.reference;
      // console.log(this.transaction_ref)
      this.postData();
     this.verifyData();
      // if (response.status == "200") {
      //   const ref = response.trxref;
      //   this.response({ ref });
      // } else {
      //   alert("Something went wrong! Please try again");
      // }
    },
    close: function() {
      console.log("Payment closed");
    },
    
    postData() {
      axios
        .post(
          "http://class54-backend.herokuapp.com/admin/activate",
        {
          phone_no: this.phone,
          serial: this.serial, // J8F8-F73-C61
          transaction_ref: this.transaction_ref,
          machineid: this.machineid, // YUIHBH7876JJK
          amount: this.amount.toString()
        }
        )
        .then((result) => {
          console.log(result);
        });
      this.phone = "";
      
    },
     verifyData() {
      axios
        .post(
          "http://class54-backend.herokuapp.com/admin/desktop-subscription/payment/verification",
        {
          transaction_ref: this.transaction_ref,
        }
        )
        .then((result) => {
          console.log(result);
        });
      this.phone = "";
      this.$router.push("/loader");
    },
  },
};
</script>

<style>
/* Full-width input fields */
input[type="tel"] {
  width: 100%;
  padding: 10px;
  margin: 5px 0 22px 0;
  display: inline-block;
  border: none;
  border-radius: 4px;
 background-color: #ddd;
}

input[type="tel"]:focus {
  background-color: #fff;
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

.form {
  margin-top: 150px;
}
.form h5 {
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
