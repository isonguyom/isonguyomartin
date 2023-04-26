<!-- eslint-disable vue/multi-word-component-names -->
<template>
    <section class="section-wrapper Hero">
        <div class="hero-text">
            <h1 class="hero-caption caption">Frontend Developer</h1>
            <div class="para hero-para">
                <p>
                    Hey, my name is Martin Isonguyo, and I am a frontend developer from Nigeria. I believe that web
                    applications could be minimal yet effective and reflective.
                </p>
                <p>
                    My motivation is that of a problem solver who leverages digital tools and skills to solve problems. I am
                    passionate about developing digital resources and accelerating their adoption in the maritime industry.
                </p>
                <p>I am available to learn, work, connect, build, and grow.</p>
            </div>
            <div class="socials">
                <a v-for="(link) in socialLinks" :key="link.name" class="social-link" :href="link.link" :title="link.name">
                    <Icon :icon="link.icon" width="25" />
                </a>
                <!-- <a class="social-link" href="files/martin-isonguyo-cv.pdf" title="Download CV" download>
                    <Icon icon="ph:file-text-light" width="25" />
                </a> -->
            </div>
            <div class="btn-wrapper">
                <Button link="#contact" text="Hire me" />
            </div>
        </div>
        <div class="circle" />
    </section>
</template>

<script>
import { Icon } from '@iconify/vue';
import gsap from 'gsap'
import { ScrollTrigger } from "gsap/ScrollTrigger";

gsap.registerPlugin(ScrollTrigger);

import Button from './Button.vue';

export default {
    // eslint-disable-next-line vue/no-reserved-component-names
    components: { Button, Icon },
    data() {
        return {
            socialLinks: [
                { name: 'Github', icon: 'ph:github-logo-light', link: 'https://github.com/isonguyom' },
                { name: 'Behance', icon: 'ph:behance-logo-light', link: 'https://www.behance.net/martinisonguyo' },
                { name: 'Twitter', icon: 'ph:twitter-logo-light', link: 'https://twitter.com/IsonguyoM' }
            ]
        }
    },

    mounted() {
        var tl = gsap.timeline({
            scrollTrigger: {
                trigger: ".Hero",
            }
        });

        tl.from(".Hero", {
            duration: 0.5,
            opacity: 0,
        })
            .from(".hero-caption", {
                delay: 0.2,
                duration: 1,
                ease: 'bounce.out',
                y: -200,
                opacity: 0,
            })
            .from(".hero-para", {
                duration: .7,
                x: -50,
                opacity: 0,
            })
            .from(".social-link", {
                duration: 1,
                stagger: .2,
                opacity: 0
            })
            .from(".btn-wrapper", {
                duration: 0.7,
                y: 200,
                opacity: 0,
            })
            .from(".circle", {
                duration: 1,
                scale: 0,
                opacity: 0
            });
    },
}
</script>


<style scoped lang="scss">
.Hero {
    // background: url('/images/martin.png') no-repeat center;
    background-size: contain;
    background-color: #0a010ed5;
    height: 113vh !important;
    background-blend-mode: soft-light;
    overflow: hidden;

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

            p {
                margin-bottom: 8px;
            }
        }

        .socials {
            margin: 40px 0 50px;
            display: flex;
            display: -webkit-flex;

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

        .btn-wrapper {
            width: fit-content;
            height: fit-content;
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

        .hero-text {
            width: 70%;

            .hero-caption {
                font-size: 4vw;
            }

            .hero-para {
                line-height: 1.4em;
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