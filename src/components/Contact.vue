<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <section class="section-wrapper Contact">
    <h3 class="title1">Contact me</h3>
    <div class="form-wrapper">
      <div ref="feedback" class="feedback">{{ feedbackMessage }}</div>
      <form id="contactForm" @submit.prevent="sendEmail">
        <div class="form-control" v-for="item in inputs" :key="item.id">
          <label :for="item.id">{{ item.label }}</label>
          <input
            :type="item.type"
            :name="item.id"
            :id="item.id"
            v-model="item.value"
            :placeholder="item.placeholder"
            required
          />
        </div>
        <div class="form-control">
          <label for="contactMessage">Message</label>
          <textarea
            name="contactMessage"
            id="contactMessage"
            v-model="contactMessage"
            cols="30"
            rows="10"
            placeholder="Your Message"
            required
          ></textarea>
        </div>
        <button type="submit">Send Message</button>
      </form>
    </div>

    <p class="copyright">© {{ copyrightYear }} | Martin Isonguyo</p>
  </section>
</template>

<script>
import emailjs from 'emailjs-com'
import { gsap } from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'

gsap.registerPlugin(ScrollTrigger)

export default {
  data() {
    return {
      copyrightYear: new Date().getFullYear(new Date()),
      feedbackMessage: '',
      contactName: '',
      contactEmail: '',
      contactSubject: '',
      contactMessage: '',
      inputs: [
        { id: 'contactName', type: 'text', label: 'Name', placeholder: 'Your Name' },
        { id: 'contactEmail', type: 'email', label: 'Email', placeholder: 'Your Email' },
        { id: 'contactSubject', type: 'text', label: 'Subject', placeholder: 'Subject' }
      ]
    }
  },

  mounted() {
    gsap.from('.Contact', {
      scrollTrigger: '.Contact',
      delay: 0.5,
      duration: 1,
      opacity: 0,
      stagger: 0.2
    })
  },

  methods: {
    sendEmail(e) {
      try {
        emailjs.sendForm('service_tn8g7d4', 'template_n7mt6si', e.target, 'WSDDECr6b9S02Oa1T', {
          contactName: this.contactName,
          contactEmail: this.contactEmail,
          contactSubject: this.contactSubject,
          contactMessage: this.contactMessage
        })

        this.$refs.feedback.classList.remove('error')
        this.feedbackMessage = 'Message sent successfully'
      } catch (error) {
        console.log({ error })
        this.$refs.feedback.classList.add('error')
        this.feedbackMessage = error + 'Message sent successfully'
      }
      // Reset form field
      this.contactName = ''
      this.contactEmail = ''
      this.contactSubject = ''
      this.contactMessage = ''
    }
  }
}
</script>

<style scoped lang="scss">
.Contact {
  background: url('/images/contact-bg.jpg') center fixed;
  background-size: cover;
  background-color: #0a010e85;
  background-blend-mode: soft-light;
  padding-bottom: 20px;

  .title1 {
    color: var(--title-light);
  }

  .form-wrapper {
    width: 100%;
    background: linear-gradient(to bottom right, #111111, #11111165);
    border-radius: var(--border-radius);
    padding: 1em;
    margin: 0 auto;

    .feedback {
      padding: 1em;
      color: green;

      &.error {
        color: red;
      }
    }

    #contactForm {
      width: 100%;

      label {
        color: var(--text-light);
        display: block;
        margin-bottom: 1px;
      }

      input,
      textarea,
      button {
        width: 100%;
        padding: 1em;
        border-radius: var(--border-radius);
        border: 1px solid #2b2b2b1f;
        margin-bottom: 10px;
        background-color: #b026e213;
        transition: border-color 0.5s ease;
        color: var(--title-light);

        &:placeholder {
          color: var(--text-dark);
        }

        &:hover {
          border: 1px solid var(--secondary-color);
        }
      }

      button {
        border: none;
        background: var(--primary-gradient);
        color: var(--title-light);
        cursor: pointer;
        transition: all 0.5s ease;
        margin: 0 auto;
        display: block;
        width: 70vw;

        &:hover {
          text-decoration: none;
          border: none;
          background-color: var(--secondary-color);
        }
      }
    }
  }

  .copyright {
    color: var(--text-light);
    margin-top: 30px;
    font-size: 0.9rem;
  }
}

@media screen and (min-width: 480px) {
  .Contact {
    .form-wrapper {
      width: 80%;

      #contactForm {
        button {
          width: 45vw;
        }
      }
    }
  }
}

@media screen and (min-width: 992px) {
  .Contact {
    .form-wrapper {
      width: 50%;

      #contactForm {
        button {
          width: 25vw;
        }
      }
    }
  }
}
</style>
