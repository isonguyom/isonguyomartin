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
      <div class="projects-inner">
        <div class="project" v-for="project in projects" :key="project.name">
          <img class="project-img" :src="`images/${project.image}.png`" :alt="project.name" />
          <a :href="project.link" class="project-caption">{{ project.caption }}</a>
        </div>
        <a href="https://github.com/isonguyom/" class="btn-wrapper">
          <Icon icon="material-symbols:read-more" width="50" />
        </a>
      </div>
    </div>
  </section>
</template>

<script>
import { gsap } from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'
import { Icon } from '@iconify/vue'

gsap.registerPlugin(ScrollTrigger)

export default {
  // eslint-disable-next-line vue/no-reserved-component-names
  components: { Icon },
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
    margin: 0 auto 50px;

    .title1 {
      margin-bottom: 10px;
    }
  }

  .projects-inner {
    width: 100%;
    display: flex;
    display: -webkit-flex;

    .project {
      height: fit-content;
      border-radius: var(--border-radius);
      //   padding: 5px;
      background: #ffec8e27;
      //   overflow: hidden;
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

    .btn-wrapper {
      display: flex;
      align-items: center;
      justify-content: center;
      color: var(--text-dark);
      border: 0;
      background: transparent;
      margin: 0 auto;
      cursor: pointer;

      &:hover {
        color: var(--secondary-color);
      }
    }
  }

  #seeBtn {
    margin: auto;
  }
}

@media screen and (min-width: 768px) {
  .Projects {
    .projects-header {
      width: 60%;
      margin-left: auto;
      margin-right: auto;
    }

    .projects-inner {
      .project {
        width: 50%;
      }
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
