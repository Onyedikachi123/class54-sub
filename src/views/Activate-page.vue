<template>
  <div class="Download-page">
    <Navbar />

    <div class="activate-wrapper">
      <v-container>
        <v-row justify="center" class="mt-9">
          <section class="Activate__content animate__animated animate__zoomIn">
            <div class="Activate__title">
              <h4>Activate your App</h4>
            </div>
            <v-container>
              <v-layout row wrap>
                <v-flex xs12 md7>
                  <v-container>
                    <form class="activate-form">

                      <label for="number">10-Digit unique serial number</label>
                      <input
                        type="text"
                        placeholder="e.g. W435-635-773"
                        name="number"
                        id="number"
                        required
                      />
                      <label for="phone number">Phone Number</label>
                      <input
                        type="text"
                        placeholder="eg: 0810242546724"
                        name="number"
                        id="number"
                        required
                      />
                      <button type="submit" class="numberbtn mb-3">
                        Proceed
                      </button>
                    </form>
                  </v-container>
                </v-flex>
                <v-flex xs12 md5>
                  <v-container>
                    <div class="activate-list">
                      <h5>How to Activate Software</h5>
                      <ul>
                        <li class="mb-3">
                          Download and follow the installation wizard till
                          installation is completed.
                        </li>
                        <li class="mb-3">
                          Upon successful installion, launch the app and
                          navigate to activation.
                        </li>
                        <li>
                          Copy the Unique serial number displayed and enter it
                          here
                        </li>
                      </ul>
                    </div>
                  </v-container>
                </v-flex>
              </v-layout>
            </v-container>
          </section>
        </v-row>
      </v-container>
      <Footer />
    </div>
  </div>
</template>

<script>
import Navbar from "../components/Navbar";
import Footer from "../components/Footer";
export default {
  name: "Activate",
  components: {
    Navbar,
    Footer,
  },
  data: () => ({
    errorMessages: "",
    number: null,
    phoneNumber: null,
    formHasErrors: false,
  }),

  computed: {
    form() {
      return {
        number: this.number,
        phoneNumber: this.phoneNumber,
      };
    },
  },

  watch: {
    number() {
      this.errorMessages = "";
    },
  },

  methods: {
    phoneNumberCheck() {
      this.errorMessages =
        this.phoneNumber && !this.number ? `Hey! I'm required` : "";

      return true;
    },
    resetForm() {
      this.errorMessages = [];
      this.formHasErrors = false;

      Object.keys(this.form).forEach((f) => {
        this.$refs[f].reset();
      });
    },
    submit() {
      this.formHasErrors = false;

      Object.keys(this.form).forEach((f) => {
        if (!this.form[f]) this.formHasErrors = true;

        this.$refs[f].validate(true);
      });
    },
  },
};
</script>

<style>
.activate-wrapper {
  background-color: #f4faf6;
  padding-top: 100px;
}
form {
  margin-top: 0 !important;
}
.form-activate {
  margin: 30px 15px !important;
}
.Activate__content {
  width: 800px;
  background: #ffffff;
  box-shadow: 0px 3px 4px rgba(0, 35, 16, 0.1);
  border-radius: 4px;
  padding: 20px 30px;
}
.Activate__content .Activate__title h4 {
  font-weight: 700;
  font-size: 24px;
  color: #00506b;
  margin: 10px 20px;
}
input[type="text"] {
  width: 100%;
  padding: 10px;
  margin: 5px 0 22px 0;
  display: inline-block;
  border: none;
 background: #FAFAFA;
  border: 1px solid #e8e8e8;
  border-radius: 4px;
}

::-webkit-input-placeholder {color: #BDBDBD;;} /* Chrome/Opera/Safari */
::-moz-placeholder { color: #BDBDBD;;} /* Firefox 19+ */
:-ms-input-placeholder { color: #BDBDBD;;} /* IE 10+ */
:-moz-placeholder {color: #BDBDBD;;} 

input[type="text"]:focus {
   outline: none !important;
  background-color: #fff;
  border: 1px solid #29CC7A !important;
  transition: background-color 0.5s ease;
}

/* Set a style for the submit button */
.numberbtn {
  padding: 10px 12px;
  color: #fff;
  border: none;
  cursor: pointer;
  width: 100%;
  background: #29cc7a;
  border-radius: 4px;
}

.numberbtn:hover {
  opacity: 1;
}
.activate-list {
  background: #f5fffa;
  border-radius: 4px;
  padding: 20px 30px;
  width: 279px;
  margin-top: -44px;
  height: 277px;
}
.activate-list ul li {
  font-size: 14px;
  font-style: normal;
  font-weight: 400;
  line-height: 20px;
}
.activate-list h5 {
  font-size: 16px;
  font-weight: 700;
  font-style: normal;
}
@media (max-width: 600px) {
  .Activate__content {
    width: 100%;
    margin: 0 15px;
  }
  .activate-list {
    margin-top: 10px;
    width: 300px;
  }
}
</style>
