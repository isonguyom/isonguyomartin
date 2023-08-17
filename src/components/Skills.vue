<!-- eslint-disable vue/multi-word-component-names -->
<template>
    <section class="container section-wrapper">
        <div class="Skills">
            <h3 class="title1">How i can serve you</h3>
            <div class="skills-wrapper">
                <div class="skill" :class="{ primaryBg: skill.activeBg }" v-for="skill in skills" :key="skill.title">
                    <div class="skill-header">
                        <Icon class="icon" :icon="skill.icon" width="80" stroke-width="2" />
                        <h4 class="skill-title">{{ skill.title }}</h4>
                    </div>
                    <p class="skill-text">{{ skill.text }}</p>
                    <p>Tools: {{ skill.tools }}</p>
                </div>
            </div>
        </div>
        <!-- <div class="Tools">
      <div class="tool" v-for="tool in tools" :key="tool.caption">
        <img class="tool-icon" :src="`images/${tool.icon}.svg`" :alt="tool.caption" />
        <p class="tool-caption">{{ tool.caption }}</p>
      </div>
    </div> -->
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
                    icon: 'iconoir:dev-mode-laptop',
                    activeBg: true,
                    text: 'I build amazing responsive websites using a mobile-first approach while following best practices. My core frontend tools are HTML, CSS, JavaScript, and VueJS.',
                    tools: 'HTML/CSS, JavaScript, Vuejs, Node.js, Express.js, MongoDB, SCSS, Bootstrap, Figma'
                },
                {
                    title: 'Big Data',
                    icon: 'arcticons:wordpress',
                    activeBg: false,
                    text: 'WordPress is a powerful CMS platform that accounts for over 43.2% of all websites. It is rich in plugins, which makes it ideal for your next website.',
                    tools: 'Hadoop, Hive, Spark, MS Excel, MongoDB'
                },
                {
                    title: 'Design',
                    icon: 'fluent:design-ideas-16-regular',
                    activeBg: false,
                    text: "I consider a design's ability to effectively communicate in its simplest and cleanest form significant. I may not be your regular GUI designer, but yeah! I can do a job.",
                    tools: 'Figma, Corel Draw'
                },
                {
                    title: 'Maritime',
                    icon: 'fluent:design-ideas-16-regular',
                    activeBg: false,
                    text: "I consider a design's ability to effectively communicate in its simplest and cleanest form significant. I may not be your regular GUI designer, but yeah! I can do a job.",
                    tools: 'Hadoop, Hive, Spark, MS Excel, MongoDB'
                }
            ],
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
    font-size: 1.3rem;
    line-height: 30px;

    .skills-wrapper {
        display: flex;
        display: -webkit-flex;
        flex-direction: column;
        align-items: center;

        .skill {
            width: 80vw;
            margin-bottom: 40px;
            padding: 40px 3%;

            .skill-header {
                display: flex;
                display: -webkit-flex;
                align-items: center;
                margin-bottom: 20px;

                .icon {
                    color: var(--primary-color);
                }

                .skill-title {
                    line-height: 1.2em;
                    margin-left: 10px;
                }
            }

            &:last-child {
                margin-bottom: 0;
            }

            &.primaryBg {
                background: var(--primary-color);

                .icon {
                    color: var(--secondary-color);
                }
            }
        }
    }
}


@media screen and (min-width: 768px) {
    .Skills {
        .skills-wrapper {
            flex-direction: row;
            justify-content: center;
            align-items: normal;
            flex-wrap: wrap;

            .skill {
                width: 50%;
            }
        }
    }
}

@media screen and (min-width: 992px) {
    .Skills {
        font-size: 2rem;
        line-height: 55px;

        .title1 {
            margin-bottom: 35px;
        }

        .skills-wrapper {
            flex-direction: row;
            justify-content: center;
            align-items: normal;

        }
    }
}
</style>
