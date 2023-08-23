<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <section class="container section-wrapper">
    <div class="Skills">
      <h3 class="title1">Specializations</h3>
      <div class="skills-wrapper">
        <div class="skill" :class="skill.class" v-for="skill in skills" :key="skill.title">
          <div class="skill-header">
            <Icon class="icon" :icon="skill.icon" width="80" stroke-width="2" />
            <h4 class="skill-title">{{ skill.title }}</h4>
          </div>
          <p class="skill-text">{{ skill.text }}</p>
          <p class="tools"><b>Tools:</b> {{ skill.tools }}</p>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import { Icon } from '@iconify/vue'
import { gsap } from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'

gsap.registerPlugin(ScrollTrigger)

export default {
  components: { Icon },
  data() {
    return {
      skills: [
        {
          title: 'Web Development',
          class: 'web',
          icon: 'iconoir:dev-mode-laptop',
          text: 'With a solid foundation in HTML, CSS, and JavaScript, I am capable of building user-friendly interfaces that deliver exceptional user experiences.',
          tools:
            'HTML/CSS, JavaScript, Vuejs, Node.js, Express.js, MongoDB, SCSS, Bootstrap, Git/Github, Wordpress'
        },
        {
          title: 'Big Data',
          class: 'data',
          icon: 'eos-icons:big-data-outlined',
          text: 'I extract, analyse, and make sense of large and complex data sets and leverage them to solve problems, drive innovation, and make data-driven decisions.',
          tools: 'Python, Hadoop, Hive, Spark, SQL, MS Excel'
        },
        {
          title: 'Design',
          class: 'design',
          icon: 'fluent:design-ideas-16-regular',
          text: "I consider a design's ability to effectively communicate in its simplest and cleanest form significant. I may not be your regular GUI designer, but yeah! I can do a job.",
          tools: 'Figma, Corel Draw, Inkscape'
        },
        {
          title: 'Marine-tech',
          class: 'marine',
          icon: 'ri:ship-line',
          text: 'My academic background in marine engineering, coupled with my tech skills, has fueled an enthusiasm for providing digital solutions to challenges in the maritime industry. \rEmbarking on a marine-tech project: I am glad to be on the team.',
          tools: 'C++, Google Drive'
        }
      ]
    }
  },

  mounted() {
    // const tl = gsap.timeline({
    //   scrollTrigger: {
    //     trigger: '.Skills'
    //   }
    // })
    // tl.from('.skill', {
    //   x: -500,
    //   duration: 2,
    //   stagger: 0.2,
    //   opacity: 0
    // }).from('.title1', {
    //   delay: 0.5,
    //   duration: 1,
    //   ease: 'bounce.out',
    //   y: -100,
    //   opacity: 0
    // })
    // gsap.from('.tool', {
    //   scrollTrigger: '.Tools',
    //   delay: 0.5,
    //   duration: 3,
    //   stagger: 0.3,
    //   opacity: 0
    // })
  }
}
</script>

<style scoped lang="scss">
.container {
  width: 100%;
  height: fit-content;
}

.Skills {
  .skills-wrapper {
    display: flex;
    display: -webkit-flex;
    flex-direction: column;
    align-items: center;
    font-size: 1.2rem;

    .skill {
      width: 90vw;
      padding: 30px 5%;
      color: var(--text-light);

      .skill-header {
        display: flex;
        display: -webkit-flex;
        align-items: center;
        margin-bottom: 20px;

        .icon {
          color: var(--title-light);
        }

        .skill-title {
          font-size: 1.4rem;
          margin-left: 15px;
          text-transform: uppercase;
          color: var(--title-light);
        }
      }

      &.web {
        background: var(--primary-color);
      }

      &.data {
        background-color: var(--secondary-color);
        color: var(--text-dark);

        .skill-title {
          color: var(--title-dark);
        }

        .icon {
          color: var(--title-dark);
        }
      }

      &.design {
        background-color: #8bd18b;
        color: var(--text-dark);

        .skill-title {
          color: var(--title-dark);
        }

        .icon {
          color: var(--title-dark);
        }
      }

      &.marine {
        background-color: #0e0563;
      }

      .tools {
        margin-top: 40px;
      }
    }
  }
}

@media screen and (min-width: 768px) {
  .Skills {
    .title1 {
      text-align: left;
    }

    .skills-wrapper {
      flex-direction: row;
      justify-content: center;
      align-items: normal;
      flex-wrap: wrap;

      .skill {
        width: 50%;
        margin-bottom: 0;
      }
    }
  }
}
</style>
