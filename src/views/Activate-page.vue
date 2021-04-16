<template>
  <div class="activate-page">
    <Navbar />
    <div class="activate-wrapper">
     
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
.activate-form-wrapper {
 width: 800px;
}
.activate-wrapper {
  background-color: #f4faf6;
}
.activate-list {
  margin: 30px 15px;
  padding: 15px;
background-color: #F5FFFA !important;
border-radius: 4px;
}
.form-activate{
 margin: 30px 15px;
}
</style>
