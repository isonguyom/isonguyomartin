<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <section class="section-wrapper Hero" ref="hero">
    <div class="curve" />
    <div class="hero-text" ref="heroText">
      <div class="text-inner" ref="textInner">
        <h1 class="hero-caption caption">Frontend Developer</h1>
        <p class="para hero-para">
          Hey, I am Martin, from Nigeria. <br />I am a MEVN developer majoring in frontend (Vuejs).
          <br />
          My motivation is that of a problem solver who leverages digital tools and skills to provide
          data-driven solutions to challenging problems. <br />
          I am passionate about Marine-tech. I am available to learn, work, connect, build, and grow.
        </p>
      </div>
      <div class="text-inner-clone" ref="textInnerClone">
        <h1 class="hero-caption caption">Frontend Developer</h1>
        <p class="para hero-para">
          Hey, I am Martin, from Nigeria. <br />I am a MEVN developer majoring in frontend (Vuejs).
          <br />
          My motivation is that of a problem solver who leverages digital tools and skills to provide
          data-driven solutions to challenging problems. <br />
          I am passionate about Marine-tech. I am available to learn, work, connect, build, and grow.
        </p>
      </div>
      <div class="socials">
        <a v-for="link in socialLinks" :key="link.name" class="social-link" :href="link.link" :title="link.name">
          <Icon :icon="link.icon" width="25" />
        </a>
        <!-- <a class="social-link" href="files/martin-isonguyo-cv.pdf" title="Download CV" download>
                      <Icon icon="ph:file-text-light" width="25" />
                  </a> -->
      </div>

      <a href="#skills" class="btn-wrapper">
        <Icon icon="fluent-mdl2:down" width="30" />
      </a>
    </div>
  </section>
</template>

<script>
import { Icon } from '@iconify/vue'
import gsap from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'

gsap.registerPlugin(ScrollTrigger)

export default {
  // eslint-disable-next-line vue/no-reserved-component-names
  components: { Icon },
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
  //   const textContainerRect = this.$refs.textInner.getBoundingClientRect();
  // this.$refs.textInnerClone.style.top = `${textContainerRect.top}px`;
  // this.$refs.textInnerClone.style.left = `${textContainerRect.left}px`;
    // this.$refs.heroText.style.backgroundColor = "#662066"
    // if (this.$refs.heroText.style.backgroundColor == "#662066") {
    //     this.$refs.heroText.style.color = "white"
    // }
    // console.log(hero)
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
  padding: 3em 5.5%;
  background-color: var(--primary-color);
  min-height: 100vh;
  display: flex;
  display: -webkit-flex;
  justify-content: center;
  align-items: center;

  .hero-text {
    font-size: 1.3rem;
    text-align: center;
    background: transparent;
    position: relative;
    // mix-blend-mode: difference;

    .text-inner {
      position: relative;
      color: var(--primary-color);
     


      .para {
        font-family: var(--text-font);
        letter-spacing: 2px; 
        font-weight: 700;
        color:  var(--secondary-color);
      }
    }

    .text-inner-clone {
      position: absolute;
      width: 100%;
      top: 0;
      left: 0;
      z-index: 1;
      -webkit-text-stroke: 1px var(--secondary-color);
      // font-weight: 700;
      color: transparent;
      // mix-blend-mode: difference;


      
      .para {
        font-family: var(--text-font);
        letter-spacing: 2px;
        font-weight: 700;
        -webkit-text-stroke: 1px var(--primary-color);
      }
    }

    .hero-caption {
      margin-bottom: 25px;
      text-transform: uppercase;
      line-height: 1.3em;
    }

    .socials {
      margin: 30px auto 50px;
      display: flex;
      display: -webkit-flex;
      justify-content: center;

      .social-link {
        color: var(--title-light);
        border: 1px solid var(--text-light);
        border-radius: 50%;
        width: 45px;
        height: 45px;
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
      display: flex;
      align-items: center;
      justify-content: center;
      border: 0;
      background: transparent;
      margin: 0 auto;
      cursor: pointer;
    }
  }

  .curve {
    width: 40%;
    min-height: 100vh;
    background-color: var(--secondary-color);
    position: absolute;
    top: 0;
    right: 0;
    border-bottom-left-radius: 80%;
  }
}

@media screen and (min-width: 768px) {
  .Hero {
    .hero-text {
      width: 80%;
    }
  }
}

@media screen and (min-width: 992px) {
  .Hero {
    .hero-text {
      font-size: 1.7rem;
      line-height: 1.4em;

      .hero-caption {
        font-size: 3.3rem;
      }
    }
  }
}
</style>
