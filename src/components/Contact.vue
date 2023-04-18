<!-- eslint-disable vue/multi-word-component-names -->
<!-- eslint-disable vue/valid-template-root -->
<template>
    <section class="section-wrapper Contact">
        <h3 class="title1">Contact</h3>
        <div class="form-wrapper">
            <form id="contactForm" action="">
                <input type="text" name="contactName" id="contactName" placeholder="Your Name">
                <input type="email" name="contactEmail" id="contactEmail" placeholder="Your Email">
                <input type="text" name="contactSubject" id="contactSubject" placeholder="Subject">
                <textarea name="contactMessage" id="contactMessage" cols="30" rows="10" placeholder="Message"></textarea>
                <button type="submit">Send Message</button>
            </form>
        </div>

        <p class="copyright">© {{ copyrightYear }} | Martin Isonguyo</p>
    </section>
</template>

<script>
export default {
    data() {
        return {
            copyrightYear: new Date().getFullYear(new Date())
        }
    }
}
</script>

<style scoped lang="scss">
.Contact {
    background: url('/images/contact-bg.jpg') center;
    background-size: cover;
    background-color: #2b2b2b7c;
    background-blend-mode: soft-light;

    .title1 {
        color: var(--title-light);
    }

    .form-wrapper {
        width: 100%;
        background-color: #ffffff5b;
        border-radius: var(--border-radius);
        padding: 1.3em;
        margin: 0 auto;

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
                background-color: #2b2b2b1a;
                transition: border-color 0.5s ease;

                &::placeholder {
                    color: var(--text-dark);
                }

                &:hover {
                    border: 1px solid var(--secondary-color);
                }
            }

            button {
                border: none;
                background-color: var(--primary-color);
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
                    color: var(--title-dark);
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
                    width: 50vw;
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
                    width: 30vw;
                }
            }
        }
    }
}
</style>