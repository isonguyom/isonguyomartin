<!-- eslint-disable vue/multi-word-component-names -->
<template>
    <section class="section-wrapper Projects">

        <div class="projects-inner">
            <div class="projects-header">
                <h3 class="title1">My projects</h3>
                <p class="projects-text">Through the course of my learning, I am proud to have built and contributed to
                    these projects.</p>
            </div>

            <div class="project" v-for="project in projects" :key="project.name">
                <img class="project-img" :src="`images/${project.image}.png`" :alt="project.name">
                <a :href="project.link" class="project-caption">{{ project.caption }}</a>
            </div>
        </div>

        <Button id="seeBtn" link="https://github.com/isonguyom?tab=repositories" text="See more" />
    </section>
</template>

<script>
import { gsap } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";

gsap.registerPlugin(ScrollTrigger);
import Button from './Button.vue';

export default {
    // eslint-disable-next-line vue/no-reserved-component-names
    components: { Button },
    data() {
        return {
            projects: [
                { name: 'Vue Calculator', caption: 'Vue calculator', image: 'img-vue-calculator', link: 'https://iso-vue-calculator.netlify.app/' },
                { name: 'Tiptop', caption: 'Tiptop design agency website', image: 'img-tiptop', link: 'https://tiptopdesign.netlify.app/' },
                { name: 'World Citizen', caption: 'World citizen website', image: 'img-world-citizen', link: 'https://worldcitizendotorg.netlify.app/' },
                { name: 'Quiz App', caption: 'JavaScript Quiz App', image: 'img-js-quiz-app', link: 'https://isonguyom.github.io/quizAppJs/' },
                { name: 'Countdown Timer', caption: 'Vuejs countdown timer', image: 'img-countdown-timer', link: 'https://isonguyom.github.io/countdown-timer/' }
            ]
        }
    },

    mounted() {
        gsap.from(".project img", {
            scrollTrigger: ".project", // start the animation when ".box" enters the viewport (once)
            // scrub: 1,
            delay: .5,
            duration: 1,
            ease: 'bounce.out',
            y: -100,
            opacity: 0,
            stagger: .2
        });
    }
}
</script>

<style scoped lang="scss">
.Projects {

    .projects-inner {

        .projects-header {
            width: 100%;
            text-align: center;
            margin-bottom: 50px;

            .title1 {
                margin-bottom: 15px;
            }
        }

        .project {
            max-width: 400px;
            width: 80vw;
            height: fit-content;
            border-radius: var(--border-radius);
            padding: 5px;
            background: #ffec8e27;
            margin: 0 auto 40px;
            overflow: hidden;
            transition: padding 1s ease;

            .project-img {
                border-radius: var(--border-radius);
                display: block;
            }

            .project-caption {
                display: block;
                background-color: #ffec8edc;
                color: var(--title-dark);
                text-align: center;
                width: 100%;
                height: 100%;
                padding: 10px;
                border-radius: var(--border-radius);
                transition: opacity 1s ease;
                text-transform: capitalize;
                position: absolute;
                top: 0;
                font-size: 2.5rem;
                opacity: 0;

                &:hover {
                    text-decoration: line-through;
                }
            }

            &:hover {
                padding: 0;

                .project-caption {
                    opacity: 1;
                }
            }
        }
    }

    #seeBtn {
        margin: auto;
    }
}

@media screen and (min-width: 768px) {
    .Projects {

        .projects-inner {
            width: 100%;
            display: flex;
            display: -webkit-flex;
            flex-wrap: wrap;
            margin-bottom: 60px;

            .projects-header {
                width: 70%;
                margin-left: auto;
                margin-right: auto;
            }

            .project {
                width: 48%;
                margin-left: 0;
            }
        }
    }
}

@media screen and (min-width: 992px) {
    .Projects {

        .projects-inner {
            justify-content: space-between;
            padding-top: 80px;

            .projects-header {
                width: 33%;
                text-align: left;
                margin-right: 0;
                margin-left: 0;
                display: flex;
                display: -webkit-flex;
                flex-direction: column;
                justify-content: center;
                padding-right: 25px;
                max-width: 350px;

                .title1 {
                    text-align: left;
                }
            }

            .project {
                width: 33%;
                max-width: 350px;
                margin-left: 0;
            }
        }
    }
}
</style>