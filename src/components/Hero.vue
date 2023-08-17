<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <section class="section-wrapper Hero">
    <div class="curve" />
    <div class="hero-text">
      <h1 class="hero-caption caption">Frontend Developer</h1>
      <p class="para hero-para">
        Hey, I am Martin, from Nigeria. <br />I am a MEVN developer majoring in frontend (Vuejs).
        <br />
        My motivation is that of a problem solver who leverages digital tools and skills to provide
        data-driven solutions to challenging problems. <br />
        I am passionate about Marine-tech. I am available to learn, work, connect, build, and grow.
      </p>
      <div class="socials">
        <a
          v-for="link in socialLinks"
          :key="link.name"
          class="social-link"
          :href="link.link"
          :title="link.name"
        >
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
  </section>
</template>

<script>
import { Icon } from '@iconify/vue'
import gsap from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'

gsap.registerPlugin(ScrollTrigger)

import Button from './Button.vue'

export default {
  // eslint-disable-next-line vue/no-reserved-component-names
  components: { Button, Icon },
  data() {
    return {
      socialLinks: [
        { name: 'Github', icon: 'ph:github-logo-light', link: 'https://github.com/isonguyom' },
        {
          name: 'Behance',
          icon: 'ph:behance-logo-light',
          link: 'https://www.behance.net/martinisonguyo'
        },
        { name: 'Twitter', icon: 'ph:twitter-logo-light', link: 'https://twitter.com/IsonguyoM' }
      ]
    }
  },

  mounted() {
    // var tl = gsap.timeline({
    //   scrollTrigger: {
    //     trigger: '.Hero'
    //   }
    // })
    // tl.from('.Hero', {
    //   duration: 0.5,
    //   opacity: 0
    // })
    //   .from('.hero-caption', {
    //     delay: 0.2,
    //     duration: 1,
    //     ease: 'bounce.out',
    //     y: -200,
    //     opacity: 0
    //   })
    //   .from('.hero-para', {
    //     duration: 0.7,
    //     x: -50,
    //     opacity: 0
    //   })
    //   .from('.social-link', {
    //     duration: 1,
    //     stagger: 0.2,
    //     opacity: 0
    //   })
    //   .from('.btn-wrapper', {
    //     duration: 0.7,
    //     y: 200,
    //     opacity: 0
    //   })
    //   .from('.circle', {
    //     duration: 1,
    //     scale: 0,
    //     opacity: 0
    //   })
  }
}
</script>

<style scoped lang="scss">
.Hero {
  background-color: rgb(102, 32, 102);
  min-height: 100vh;
  display: flex;
  display: -webkit-flex;
  justify-content: center;
  align-items: center;

  .hero-text {
    font-size: 1.2em;
    text-align: center;
    line-height: 33px;

    .hero-caption {
      margin-bottom: 25px;
      text-transform: uppercase;
    }

    .socials {
      margin: 40px auto 50px;
      display: flex;
      display: -webkit-flex;
      justify-content: center;

      .social-link {
        color: var(--title-light);
        border: 1px solid var(--text-light);
        border-radius: 50%;
        width: 50px;
        height: 50px;
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
      margin: 0 auto;
    }
  }

  .curve {
    width: 50%;
    min-height: 100vh;
    background-color: rgb(230, 199, 230);
    position: absolute;
    top: 0;
    right: 0;
    border-bottom-left-radius: 100%;
  }
}

@media screen and (min-width: 768px) {
  .Hero {
    .hero-text {
      width: 70%;
      font-size: 1.3em;

      .socials {
        .social-link {
          width: 60px;
          height: 60px;
        }
      }
    }
  }
}

@media screen and (min-width: 1300px) {
  .Hero {
    .hero-text {
      width: 50%;
      line-height: 50px;
      font-size: 2em;
      font-weight: 500;

      .hero-caption {
        font-size: 4rem;
        margin-bottom: 30px;
      }
    }
  }
}
</style>
