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
                </div>
            </div>

        </div>
        <div class="Tools">
            <div class="tool" v-for="tool in tools" :key="tool.caption">
                <img class="tool-icon" :src="`images/${tool.icon}.svg`" :alt="tool.caption">
                <p class="tool-caption">{{ tool.caption }}</p>
            </div>
        </div>
    </section>
</template>

<script>
import { Icon } from '@iconify/vue';
import { gsap } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";

gsap.registerPlugin(ScrollTrigger);

export default {
    components: { Icon },
    data() {
        return {
            skills: [
                { title: 'Frontend Development', icon: 'iconoir:dev-mode-laptop', activeBg: true, text: 'Amazing websites are simple and clean. Minimalism is the concept, and minimalism is my concept.' },
                { title: 'Wordpress', icon: 'arcticons:wordpress', activeBg: false, text: 'Wordpress is the most popular CMS-based website platform. I build good and efficient wordpress websites.' },
                { title: 'UI/UX Design', icon: 'solar:window-frame-outline', activeBg: false, text: 'Although each product is unique, a good design offers it meaning and efficiently communicates with the user.' }
            ],

            tools: [
                { caption: 'Vuejs', icon: 'icon-vuejs' },
                { caption: 'JavaScript', icon: 'icon-javascript' },
                { caption: 'HTML', icon: 'icon-html' },
                { caption: 'CSS', icon: 'icon-css' },
                { caption: 'Bootstrap', icon: 'icon-bootstrap' },
                { caption: 'SCSS', icon: 'icon-scss' },
                { caption: 'jQuery', icon: 'icon-jquery' },
                { caption: 'Figma', icon: 'icon-figma' },
                { caption: 'Python', icon: 'icon-python' },
                { caption: 'C++', icon: 'icon-cpp' },
                { caption: 'GSAP', icon: 'icon-gsap' },
                { caption: 'Github', icon: 'icon-github' }
            ]
        }
    },

    mounted() {
        const tl = gsap.timeline({
            scrollTrigger: {
                trigger: ".Skills",
            }
        });
        tl.from(".skill", {
            x: -500,
            duration: 2,
            stagger: .2,
            opacity: 0,
        })
            .from(".title1", {
                delay: .5,
                duration: 1,
                ease: 'bounce.out',
                y: -100,
                opacity: 0,
            });

        gsap.from(".tool", {
            scrollTrigger: ".Tools",
            delay: 0.5,
            duration: 3,
            stagger: .3,
            opacity: 0,
        });
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

        .skill {
            max-width: 400px;
            width: 80vw;
            margin-bottom: 40px;
            background: linear-gradient(to bottom right, #111111, #11111165);
            padding: 40px 3%;
            border-radius: var(--border-radius);
            box-shadow: var(--box-shadow);

            .skill-header {
                display: flex;
                display: -webkit-flex;
                align-items: center;
                margin-bottom: 20px;

                .icon {
                    color: var(--primary-color)
                }

                .skill-title {
                    line-height: 1.2em;
                    margin-left: 10px;
                    color: var(--title-light);
                }
            }

            &:last-child {
                margin-bottom: 0;
            }

            &.primaryBg {
                background: var(--primary-gradient);

                .icon {
                    color: var(--secondary-color)
                }
            }
        }
    }
}

.Tools {
    background: linear-gradient(to top right, #b126e2, #ffec8e6c, #b026e2d0);
    color: var(--secondary-color);
    font-weight: 600;
    display: flex;
    display: -webkit-flex;
    justify-content: center;
    flex-wrap: wrap;
    min-height: fit-content;
    padding: 2vw 2vw 0;
    margin-top: 100px;

    .tool {
        display: flex;
        display: -webkit-flex;
        justify-content: center;
        align-items: center;
        width: 100%;
        max-width: 250px;
        border: 1px solid var(--secondary-color);
        height: fit-content;
        padding: 5px;
        border-radius: var(--border-radius);
        margin-bottom: 2vw;

        .tool-icon {
            display: block;
            margin-right: 4px;
            padding: 6px;
        }

        .tool-caption {
            text-transform: uppercase;
        }
    }
}


@media screen and (min-width: 556px) {
    .Tools {
        justify-content: space-between;
    }
}


@media screen and (min-width: 992px) {
    .Skills {

        .title1 {
            top: 130px;
            margin-bottom: 35px;
        }

        .skills-wrapper {
            flex-direction: row;
            justify-content: space-between;
            align-items: normal;
            padding-bottom: 70px;

            .skill {
                max-width: 290px;
                margin-bottom: 0;

                &:nth-child(even) {
                    top: 150px;
                }
            }
        }
    }


    .Tools {
        margin-top: 150px;
        padding-top: 3vw 3vw 0;
    }
}
</style>