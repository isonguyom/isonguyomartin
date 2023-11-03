<template>
    <div ref="carouselContainer" class="carousel-container projects-inner">
        <div class="project carousel-slide" v-for="(slide, index) in projects" :key="index" :ref="`slide-${index}`">
            <img class="project-img" :src="`images/${slide.image}.png`" :alt="slide.name" />
            <a :href="slide.link" class="project-caption">{{ slide.caption }}</a>
        </div>
    </div>
</template>

<script>
import { gsap, ScrollTrigger } from "gsap/all";

gsap.registerPlugin(ScrollTrigger)

export default {
    // eslint-disable-next-line vue/no-reserved-component-names
    data() {
        return {
            projects: [
                {
                    name: 'Tiptop',
                    caption: 'Tiptop design agency website',
                    image: 'tiptop',
                    link: 'https://tiptopdesign.netlify.app/'
                },
                {
                    name: 'Gallery',
                    caption: 'Drag and Drop Gallery',
                    image: 'gallery',
                    link: 'https://isonguyom.github.io/drag-and-drop-gallery/'
                },
                {
                    name: 'DummyMe',
                    caption: 'DummyMe onPage assistant',
                    image: 'dummyme',
                    link: 'https://isonguyom.github.io/dummyMe/'
                },
                {
                    name: 'Quiz App',
                    caption: 'JavaScript Quiz App',
                    image: 'img-js-quiz-app',
                    link: 'https://isonguyom.github.io/quizAppJs/'
                },
                {
                    name: 'MovieBox',
                    caption: 'MovieBox',
                    image: 'moviebox',
                    link: 'https://isonguyom.github.io/moviebox/'
                },
                {
                    name: 'World Citizen',
                    caption: 'World citizen website',
                    image: 'img-world-citizen',
                    link: 'https://worldcitizendotorg.netlify.app/'
                },
                {
                    name: 'Countdown Timer',
                    caption: 'Vuejs countdown timer',
                    image: 'img-countdown-timer',
                    link: 'https://isonguyom.github.io/countdown-timer/'
                },
                {
                    name: 'Checkout Form',
                    caption: 'Vuejs checkout form',
                    image: 'checkout-form',
                    link: 'https://isonguyom.github.io/vueCheckoutForm/'
                },
                {
                    name: 'Length Converter',
                    caption: 'Length Converter',
                    image: 'length-converter',
                    link: 'https://isonguyom.github.io/length-converter/'
                }
            ]
        }
    },

    mounted() {
        this.animateProjects()
        this.createCarousel();
    },

    methods: {
        animateProjects() {
            gsap.set(this.$refs.carouselContainer.children, { y: 100, opacity: 0 });
            gsap.to(this.$refs.carouselContainer.children, {
                y: 0,
                opacity: 1,
                stagger: 0.4,
                duration: 3,
                scrollTrigger: {
                    trigger: this.$refs.carouselContainer,
                    start: 'top center',
                    end: 'bottom top',
                    toggleActions: 'play reverse play reverse',
                },
            });
        },
        createCarousel() {
            // const tl = gsap.timeline({
            //   repeat: -1, // Repeat the animation indefinitely
            //   paused: true, // Start the animation paused
            // });

            // this.$refs.slide.forEach((slide, index) => {
            //   tl.to(slide, {
            //     duration: 1, // Animation duration in seconds
            //     x: -100 * index, // Move each slide to the left by 100% of its width
            //   });
            // });

            // tl.play();
        },
    },
}
</script>

<style scoped lang="scss">
.projects-inner {
    width: 100%;
    display: flex;
    display: -webkit-flex;
    justify-content: center;
    flex-wrap: wrap;
    gap: 40px;

    .project {
        height: fit-content;
        border-radius: var(--border-radius);
        background: #ffec8e27;
        transition: padding 1s ease;
        width: fit-content;
        box-shadow: 0px 4px 20px 0px rgba(0, 0, 0, 0.10);

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
            padding: 50px 10px;
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
</style>