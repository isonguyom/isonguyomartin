<!-- eslint-disable vue/multi-word-component-names -->
<template>
    <section class="section-wrapper Contact">
        <h3 class="title1">Contact</h3>
        <div class="form-wrapper">
            <div ref="feedback" class="feedback">{{ feedbackMessage }}</div>
            <form id="contactForm" @submit.prevent="sendEmail">
                <input type="text" name="contactName" id="contactName" v-model="contactName" placeholder="Your Name"
                    required>
                <input type="email" name="contactEmail" id="contactEmail" v-model="contactEmail" placeholder="Your Email"
                    required>
                <input type="text" name="contactSubject" id="contactSubject" v-model="contactSubject" placeholder="Subject"
                    required>
                <textarea name="contactMessage" id="contactMessage" v-model="contactMessage" cols="30" rows="10"
                    placeholder="Your Message" required></textarea>
                <button type="submit">Send Message</button>
            </form>
        </div>

        <p class="copyright">© {{ copyrightYear }} | Martin Isonguyo</p>
    </section>
</template>

<script>
import emailjs from 'emailjs-com';
import { gsap } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";

gsap.registerPlugin(ScrollTrigger);


export default {
    data() {
        return {
            copyrightYear: new Date().getFullYear(new Date()),
            feedbackMessage: '',
            contactName: '',
            contactEmail: '',
            contactSubject: '',
            contactMessage: ''
        }
    },

    mounted() {
        gsap.from(".Contact", {
            scrollTrigger: ".Contact",
            delay: .5,
            duration: 1,
            opacity: 0,
            stagger: .2
        });
    },

    methods: {
        sendEmail(e) {
            try {
                emailjs.sendForm('service_tn8g7d4', 'template_n7mt6si', e.target,
                    'WSDDECr6b9S02Oa1T', {
                    contactName: this.contactName,
                    contactEmail: this.contactEmail,
                    contactSubject: this.contactSubject,
                    contactMessage: this.contactMessage
                })

                this.$refs.feedback.classList.remove("error")
                this.feedbackMessage = 'Message sent successfully'
            } catch (error) {
                console.log({ error })
                this.$refs.feedback.classList.add("error")
                this.feedbackMessage = error + 'Message sent successfully'
            }
            // Reset form field
            this.contactName = ''
            this.contactEmail = ''
            this.contactSubject = ''
            this.contactMessage = ''
        },
    }
}
</script>

<style scoped lang="scss">
.Contact {
    background: url('/images/contact-bg.jpg') center fixed;
    background-size: cover;
    background-color: #0a010eb7;
    background-blend-mode: soft-light;
    padding-bottom: 20px;

    .title1 {
        color: var(--title-light);
    }

    .form-wrapper {
        width: 100%;
        background: linear-gradient(to bottom right, #111111, #11111165);
        border-radius: var(--border-radius);
        padding: 1.3em;
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

            input,
            textarea,
            button {
                width: 100%;
                padding: 1em;
                border-radius: var(--border-radius);
                border: 1px solid #2b2b2b1f;
                margin-bottom: 20px;
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
        margin-top: 80px;
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
            width: 60%;

            #contactForm {

                button {
                    width: 25vw;
                }
            }
        }
    }
}
</style>