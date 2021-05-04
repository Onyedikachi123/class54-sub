<template>
  <div class="Download-page">
    <Navbar />

    <div class="download-wrapper">
      <v-container>
        <v-row justify="center" no-gutters style="display: grid" class="mt-9">
          <section class="Download__content">
            <div class="download__title">
              <!-- <img
                src="../assets/JAMB 1.png"
                alt="Jamb-logo"
                class="jamb-logo"
              /> -->
              <svg width="42" height="42" viewBox="0 0 42 42" fill="none" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
                <rect width="42" height="42" fill="url(#pattern0)"/>
                <defs>
                <pattern id="pattern0" patternContentUnits="objectBoundingBox" width="1" height="1">
                <use xlink:href="#image0" transform="translate(-0.0319149) scale(0.0106383)"/>
                </pattern>
                <image id="image0" width="100" height="94" xlink:href="data:image/png;base64,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"/>
                </defs>
              </svg>

              <h4>Offline JAMB CBT Software (2021)</h4>
            </div>
            <div class="download__text">
              <p class="pt-4">
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
                <button>Download now</button>
              </div>
            </div>
            <!-- </div> -->
          </section>
          <section class="faq-section mt-9" style="margin-bottom: -100px;">
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
        <Footer />
      </v-container>
      
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
  box-shadow: 0px 3px 4px rgba(0, 38, 19, 0.1);
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
.Download-page .download-btn {
  background-color: #29cc7a;
  /* justify-content: center;
  align-items: center; */
      padding:12px;
  height: 54px;
  margin-top: 5px;
  border-radius: 4px;
  cursor: pointer;
  color: #fff;
}
.faq {
  display: block;
  width: 100%;
  max-width: 796px;
  margin: 15px auto;
  padding: 15px;
  border-radius:4px;
  box-shadow: 0px 3px 4px rgba(0, 38, 19, 0.1);
  background-color: #fff;
  cursor: pointer;
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

  width: 15px;
  height: 15px;
  background-image: url('../components/arrow-down-mint.svg');
  background-position: center;
  background-size: contain;
  background-repeat: no-repeat;
  cursor: pointer;

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
  /* .jamb-logo {
    width: 113px;
  } */
  .Download-page .download-btn{
    text-align: center;
  }

}
</style>
