<template>
  <div class="Download-page">
    <Navbar />

    <div class="download-wrapper">
      <v-container>
        <v-row justify="center" no-gutters style="display: grid" class="mt-9">
          <section class="Download__content animate__animated animate__zoomIn">
            <div class="download__title">
              <img
                src="../assets/JAMB 1.png"
                alt="Jamb-logo"
                class="jamb-logo"
              />
              <h4>Offline JAMB CBT Software (2021)</h4>
            </div>
            <div class="download__text">
              <p class="pt-9">
                Class54’s JAMB CBT PRACTICE SOFTWARE, is a Computer Testing &
                Preparatory Software, designed to help candidates prepare for
                and familiarize themselves with the coming JAMB CBT examination.
                We have error-free questions based on JAMB/UTME past and
                Expert-curated questions from 2000 to 2021. The software, which
                is totally offline (does NOT require internet connection to
                work), tracks the user, mark and score with detailed explanation
                and statistics of area of strength and weaknesses in all topics
                the mock examination.
              </p>
            </div>
            <!-- <div class="action-section"> -->
            <div class="action-group">
              <div class="download-numbers">
                <v-icon small color="dark" class="mt-3">
                  mdi-download
                </v-icon>
                <p class="mt-6 " style="font-size: 13px">23,726 Downlaods</p>
              </div>
              <div class="download-file">
                <v-icon small color="dark" class="mt-2">
                  mdi-file
                </v-icon>
                <p class="mt-6" style="font-size: 13px">124MB</p>
              </div>
              <div class="download-btn">
                <button>Downlaod now</button>
              </div>
            </div>
            <!-- </div> -->
          </section>
          <section class="faq-section mt-9">
            <h4 class="mb-4">Frequently asked questions</h4>
            <div class="faqs">
            <FAQ 
            v-for="(faq, i) in faqs" 
            :faq="faq" 
            :index="i" 
            :key="i"
            :open="faq.open"
            @toggleOpen="toggleOpen"
            />
           </div>
          </section>
        </v-row>
      </v-container>
      <Footer />
    </div>
    
  </div>
</template>
<script>
import Navbar from "@/components/Navbar";
import FAQ from '../components/FAQ'
import Footer from "@/components/Footer"
export default {
  name: "Subscription",
  components: {
    Navbar,
    FAQ,
    Footer
  },
  data () {
    return {
      faqs: [
        {
          question: "Does this software need Internet to work?",
          answer: "No. The software works completely offline. After installation and activation, user can use the app while the system is completely offline.",
          open: false
        },
        {
          question: "For how long can I use this Software?",
          answer: "Lorem Ipsum is simply dummy text of the printing and typesetting industry.",
          open: false
        },
        {
          question: "Can Install the software on multiple Computer Systems?",
          answer: "Lorem Ipsum is simply dummy text of the printing and typesetting industry.",
          open: false
        },
        {
          question: "Does the App contain all the needed subjects?",
          answer: "Lorem Ipsum is simply dummy text of the printing and typesetting industry.",
          open: false
        }
      ]
    }
  },
  methods: {
    toggleOpen: function (index) {
      this.faqs = this.faqs.map((faq, i) => {
        if (index === i) {
          faq.open = !faq.open
        } else {
          faq.open = false;
        }

        return faq;
      })
    }
  }
};


</script>

<style>
.download-wrapper {
  background-color: #f4faf6;
  padding-top: 100px;
}
.Download-card {
  margin-top: 50px;
  padding: 15px 25px;
}
.Download__content {
  width: 800px;
  /* height: 397px; */
  background: #ffffff;
  box-shadow: 0px 3px 4px rgba(0, 35, 16, 0.1);
  border-radius: 4px;
  /* border: 1px solid #ccc; */
  padding: 20px 30px;
}
.Download__content .download__title {
  display: flex;
}
.Download__content .download__title h4 {
  font-weight: 700;
  font-size: 24px;
  color: #00506b;
  margin: 10px 20px;
}
.jamb-logo {
  width: 50px;
}
.download__text p {
  text-align: justify;
  font-weight: 400;
  font-size: 16px;
  font-style: normal;
  line-height: 25.6px;
}

.action-group {
  display: flex;
  grid-gap: 30%;
}
.action-group p {
  padding-left: 2px;
}
.action-group .download-numbers {
  display: flex;
}
.action-group .download-file {
  display: flex;
}
.action-group button {
  background-color: #29cc7a;
  justify-content: center;
  align-items: center;
  padding: 8px 10px;
  margin-top: 14px;
  border-radius: 4px;
  color: #fff;
}
.faq {
  display: block;
  width: 100%;
  max-width: 796px;
  margin: 15px auto;
  padding: 15px;
  border-radius:8px;
  box-shadow: 0px 0px 10px rgba(0,0,0,0.2);
  background-color: #fff;
}
.faq .question {
  position: relative;
  color: #3c3c3c;
  font-size: 20px;
  transition: all 0.4s linear;
}

.faq .question::after {
  content: '';

  position: absolute;
  top: 50%;
  right: 0px;
  transform: translateY(-50%)rotate(0deg);

  width: 30px;
  height: 30px;
  background-image: url('../components/arrow-down-mint.svg');
  background-position: center;
  background-size: contain;
  background-repeat: no-repeat;

  transition: all 0.4s linear;
}
.faq.open .question::after {
 transform: translateY(-50%) rotate(180deg);
}
.faq.open .question {
  margin-bottom: 15px;
}
.faq .answer {
  color: #3c3c3c;
  font-size: 18px;
  opacity: 0;
  max-height: 0px;
  overflow: hidden;
  transition: all 0.4s ease-out; 
}
.faq-section h4 {
  color: #00506b;
  font-weight: 700;
  font-size: 24px;
}
.faq.open .answer {
  opacity: 1;
  max-height: 1000px;
}
@media (max-width: 600px) {
  .Download__content {
    width: 100%;
  }
  .action-group {
    display: grid;
    grid-gap: inherit;
  }
  .jamb-logo {
    width: 113px;
  }

}
</style>
