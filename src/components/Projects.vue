<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <section class="section-wrapper Projects">
    <div class="projects-header">
      <h3 class="title1">Portfolio</h3>
      <p class="projects-text">
        Through the course of my learning, I am proud to have built and contributed to these
        projects.
      </p>
    </div>
    <div>
      <ProjectsCarousel />
      <a href="https://github.com/isonguyom/" class="btn-wrapper">
        See more
      </a>
    </div>
  </section>
</template>

<script>
import { gsap, ScrollTrigger } from "gsap/all";
import ProjectsCarousel from "./ProjectsCarousel.vue";

gsap.registerPlugin(ScrollTrigger)

export default {
  // eslint-disable-next-line vue/no-reserved-component-names
  components: { ProjectsCarousel },
  data() {
    return {
      projects: [
        {
          name: 'World Citizen',
          caption: 'World citizen website',
          image: 'img-world-citizen',
          link: 'https://worldcitizendotorg.netlify.app/'
        },
        {
          name: 'Quiz App',
          caption: 'JavaScript Quiz App',
          image: 'img-js-quiz-app',
          link: 'https://isonguyom.github.io/quizAppJs/'
        },
        {
          name: 'Countdown Timer',
          caption: 'Vuejs countdown timer',
          image: 'img-countdown-timer',
          link: 'https://isonguyom.github.io/countdown-timer/'
        }
      ]
    }
  },

  mounted() {
    // gsap.from(".project img", {
    //     scrollTrigger: ".project", // start the animation when ".box" enters the viewport (once)
    //     // scrub: 1,
    //     delay: .5,
    //     duration: 1,
    //     ease: 'bounce.out',
    //     y: -100,
    //     opacity: 0,
    //     stagger: .2
    // });

    gsap.from('.Projects .title1', {
      delay: 0.1,
      duration: 1,
      ease: 'bounce.out',
      y: -100,
      opacity: 0,
      scrollTrigger: {
        trigger: '.Projects',
        start: 'top center',
        end: 'bottom top',
        toggleActions: 'play reverse play reverse',
      },
    });
  }
}
</script>

<style scoped lang="scss">
.Projects {
  padding: 4em 0;
  font-size: 1.2rem;

  .projects-header {
    width: 80vw;
    text-align: center;
    margin: 0 auto 70px;

    .title1 {
      margin-bottom: 10px;
    }
  }

  .btn-wrapper {
    display: block;
    margin-top: 40px;
    text-align: center;
    color: var(--text-dark);
    text-decoration: underline;

    &:hover {
      color: var(--secondary-color);
    }
  }
}

@media screen and (min-width: 768px) {
  .Projects {
    .projects-header {
      width: 60%;
      margin-left: auto;
      margin-right: auto;
    }
  }
}

@media screen and (min-width: 992px) {
  .Projects {

    // line-height: 55px;
    .projects-header {
      width: 40%;
    }
  }
}
</style>
