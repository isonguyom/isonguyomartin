<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <section class="section-wrapper Blog">
    <h3 class="title1">Blog</h3>
    <div class="posts-wrapper" ref="postsWrapper">
      <div class="post" v-for="post in posts" :key="post.title">
        <img class="post-img" :src="`images/${post.image}`" :alt="post.title" />
        <div class="post-text">
          <a :href="post.link" class="post-title">{{ post.title }}</a>
          <p class="post-ecerpt">{{ post.ecerpt }}<a id="more" :href="post.link">...</a></p>
          <div class="post-footer">
            <a class="post-platform" href="">{{ post.platform }}</a><span class="post-date">{{ post.date }}</span>
          </div>
        </div>
      </div>
    </div>
    <a href="https://dev.to/isonguyom" class="btn-wrapper"> Read More </a>
  </section>
</template>

<script>
import { gsap, ScrollTrigger } from "gsap/all";

gsap.registerPlugin(ScrollTrigger);

export default {
  // eslint-disable-next-line vue/no-reserved-component-names
  data() {
    return {
      posts: [
        {
          title: 'HOW TO BUILD A MEVN APP WITH VITE FRONTEND (PART 1)',
          link: 'https://dev.to/isonguyom/mevn-257p',
          image: 'mevn-vite_cover.png',
          platform: 'dev.to',
          platformLink: 'https://dev.to/isonguyom',
          date: '7 Aug 2023',
          ecerpt:
            'Full-stack web development describes the process of building the frontend and backend'
        },
        {
          title: 'HOW TO BUILD A MEVN APP WITH VITE FRONTEND (PART 2)',
          link: 'https://dev.to/isonguyom/how-to-build-a-mevn-app-with-vite-frontend-part-2-2lh8',
          image: 'mevn-vite_cover.png',
          platform: 'dev.to',
          platformLink: 'https://dev.to/isonguyom',
          date: '16 Aug 2023',
          ecerpt:
            'We want our applications to interact with each other and for our frontend to be accessible'
        },
        {
          title: 'HOW TO BUILD A MEVN APP WITH VITE FRONTEND (PART 3)',
          link: 'https://dev.to/isonguyom/how-to-build-a-mevn-app-with-vite-frontend-part-3-j9m',
          image: 'mevn-vite_cover.png',
          platform: 'dev.to',
          platformLink: 'https://dev.to/isonguyom',
          date: '21 Aug 2023',
          ecerpt: 'Congratulations! You have successfully developed your MEVN CRUD application'
        }
      ]
    }
  },

  methods: {
    animatePosts() {
      gsap.set(this.$refs.postsWrapper.children, { y: 100, opacity: 0 });
      gsap.to(this.$refs.postsWrapper.children, {
        y: 0,
        opacity: 1,
        stagger: 0.4,
        duration: 3,
        scrollTrigger: {
          trigger: this.$refs.postsWrapper,
          start: 'top bottom',
          end: 'bottom top',
          toggleActions: 'play reverse play reverse',
        },
      });
    }
  },

  mounted() {
    this.animatePosts()
    gsap.from('.Blog .title1', {
      delay: 0.5,
      duration: 1,
      ease: 'bounce.out',
      y: -100,
      opacity: 0,
      scrollTrigger: {
        trigger: '.Blog',
        start: 'top center',
        end: 'bottom top',
        toggleActions: 'play reverse play reverse',
      },
    });

  }
}
</script>

<style scoped lang="scss">
.Blog {
  min-height: fit-content;

  .posts-wrapper {
    margin: 10px 0;
    display: flex;
    display: -webkit-flex;
    flex-direction: column;
    align-items: center;
    gap: 20px;

    .post {
      max-width: 400px;
      width: 80vw;
      height: fit-content;
      background: var(--primary-color);
      border-radius: var(--border-radius);
      border: 1px solid rgb(221, 220, 220);
      transition: all 0.5s ease-in;
      box-shadow: 0px 4px 20px 0px rgba(0, 0, 0, 0.10);

      .post-img {
        height: 220px;
      }

      .post-text {
        padding: 1em;
        color: var(--text-light);

        .post-title {
          display: block;
          margin-bottom: 10px;
          color: var(--title-light);
          font-weight: 600;
          text-transform: uppercase;

          &:hover {
            color: var(--secondary-color);
          }
        }

        .post-ecerpt {
          #more {
            letter-spacing: 3px;
          }
        }

        .post-footer {
          margin-top: 30px;
          display: flex;
          display: -webkit-flex;
          justify-content: space-between;
          align-items: center;
          color: #a7a4a4;

          a {
            color: #a7a4a4;
          }
        }
      }
    }
  }

  .btn-wrapper {
    display: block;
    color: var(--text-dark);
    margin-top: 40px;
    text-align: center;
    text-decoration: underline;

    &:hover {
      color: var(--secondary-color);
    }
  }
}

@media screen and (min-width: 768px) {
  .Blog {
    .title1 {
      text-align: left;
    }

    .posts-wrapper {
      flex-direction: row;
      justify-content: space-between;
      flex-wrap: wrap;
      align-items: normal;

      .post {
        max-width: 45%;
        width: 45%;
      }
    }
  }
}

@media screen and (min-width: 992px) {
  .Blog {
    .posts-wrapper {
      .post {
        max-width: 330px;
        width: 30%;
        display: flex;
        display: -webkit-flex;
        flex-direction: column;
        justify-content: center;
      }
    }
  }
}
</style>
