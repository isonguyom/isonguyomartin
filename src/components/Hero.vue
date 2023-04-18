<!-- eslint-disable vue/multi-word-component-names -->
<template>
    <section class="section-wrapper Hero">
        <div class="hero-text">
            <h1 class="hero-caption caption">Frontend Developer</h1>
            <p class="para hero-para">
                It all started with a desire to understand how the web works and the technology behind this virtual-reality
                environment. Therefore, being able to build with some of these tools today feels good.
                I am a graduate of Marine Engineering. So you can understand my enthusiasm about digitalization in the
                maritime industry and my eagerness to contribute to any related project.
                From Akwa Ibom State, Nigeria, Martin is ready to learn, connect, build, and grow.
            </p>
            <div class="socials">
                <a v-for="(link) in socialLinks" :key="link.name" class="social-link" :href="link.link"
                    :title="link.name"><svg-icon type="mdi" :path="link.icon"></svg-icon></a>
                <a class="social-link" href="files/martin-isonguyo-cv.pdf" title="Download CV" download><svg-icon type="mdi"
                        :path="fileIconPath"></svg-icon></a>
            </div>
            <Button link="#" text="Hire me" />
        </div>
        <div class="circle" />
    </section>
</template>

<script>
import SvgIcon from '@jamescoyle/vue-icon';
import { mdiFileDocumentOutline, mdiTwitter, mdiGithub, mdiAlphaB } from '@mdi/js';


import Button from './Button.vue';

export default {
    // eslint-disable-next-line vue/no-reserved-component-names
    components: { Button, SvgIcon },
    data() {
        return {
            fileIconPath: mdiFileDocumentOutline,
            socialLinks: [
                { name: 'Github', icon: mdiGithub, link: 'https://github.com/isonguyom' },
                { name: 'Behance', icon: mdiAlphaB, link: 'https://www.behance.net/martinisonguyo' },
                { name: 'Twitter', icon: mdiTwitter, link: 'https://twitter.com/IsonguyoM' },
            ]
        }
    }
}
</script>


<style scoped lang="scss">
.Hero {
    background: url('/images/martin-grayscale.png') no-repeat center;
    background-size: contain;
    background-color: #1b1b1b;
    height: 115vh !important;
    background-blend-mode: soft-light;

    .hero-text {
        position: absolute;
        top: 50%;
        left: 0;
        transform: translate(0, -50%);
        -ms-transform: translate(0, -50%);
        padding: 3em 5%;

        .hero-caption {
            color: var(--primary-color);
            margin-bottom: 25px;
            text-transform: uppercase;
            line-height: 1.3em;
            font-size: 6vw;
        }

        .hero-para {
            color: var(--text-light);
            line-height: 1.6em;
        }

        .socials {
            margin: 40px 0 50px;
            display: flex;

            .social-link {
                color: var(--title-light);
                border: 1px solid var(--text-light);
                border-radius: 50%;
                width: 40px;
                height: 40px;
                display: flex;
                display: -webkit-flex;
                align-items: center;
                justify-content: center;
                margin-right: 1.5em;
                transition: color border-color 0.5s ease;

                &:last-child {
                    margin-right: 0;
                }


                &:hover {
                    text-decoration: none;
                    color: var(--secondary-color);
                    border-color: var(--secondary-color);
                }
            }
        }
    }

    .circle {
        display: none;
    }
}

@media screen and (min-width: 480px) {
    .Hero {

        .hero-text {

            .hero-caption {
                font-size: 5vw;
            }
        }
    }
}

@media screen and (min-width: 768px) {
    .Hero {
        overflow-x: hidden;

        .hero-text {
            width: 70%;

            .hero-caption {
                font-size: 4vw;
            }

            .hero-para {
                line-height: 1.8em;
            }
        }

        .circle {
            display: block;
            width: 40vw;
            height: 40vw;
            border: 10vw solid #d9d9d92a;
            border-radius: 50%;
            position: absolute;
            top: 50%;
            right: 0;
            transform: translate(30%, -50%);
            -ms-transform: translate(-50%, -50%);
        }
    }
}

@media screen and (min-width: 992px) {
    .Hero {
        height: 110vh;

        .hero-text {
            width: 50%;

            .hero-caption {
                font-size: 2rem;
            }
        }
    }
}
</style>