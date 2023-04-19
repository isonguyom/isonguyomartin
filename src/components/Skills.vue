<!-- eslint-disable vue/multi-word-component-names -->
<template>
    <div class="container">
        <section class="section-wrapper Skills">
            <h3 class="title1">How i can serve you</h3>
            <div class="skills-wrapper">
                <div class="skill" :class="{ primaryBg: skill.activeBg }" v-for="skill in skills" :key="skill.title">
                    <div class="skill-header">
                        <Icon class="icon" :icon="skill.icon" width="80" stroke-width="2"/>
                        <h4 class="skill-title">{{ skill.title }}</h4>
                    </div>
                    <p class="skill-text">{{ skill.text }}</p>
                </div>
            </div>

        </section>
        <section class="section-wrapper Tools">
            <div class="tool" v-for="tool in tools" :key="tool.caption">
                <img class="tool-icon" :src="`images/${tool.icon}.svg`" :alt="tool.caption">
                <p class="tool-caption">{{ tool.caption }}</p>
            </div>
        </section>
    </div>
</template>

<script>
import { Icon } from '@iconify/vue';

export default {
    components: {Icon},
    data() {
        return {
            skills: [
                { title: 'Frontend Development', icon: 'iconoir:dev-mode-laptop', activeBg: true, text: 'Lorem ipsum dolor sit amet consectetur. Convallis ultrices nunc consectetur ipsum laoreet neque ut arcu. In duis ut varius pulvinar ornare aliquet dui quis con' },
                { title: 'Wordpress', icon: 'arcticons:wordpress', activeBg: false, text: 'Lorem ipsum dolor sit amet consectetur. Convallis ultrices nunc consectetur ipsum laoreet neque ut arcu. In duis ut varius pulvinar ornare aliquet dui quis con' },
                { title: 'UI/UX Design', icon: 'solar:window-frame-outline', activeBg: false, text: 'Lorem ipsum dolor sit amet consectetur. Convallis ultrices nunc consectetur ipsum laoreet neque ut arcu. In duis ut varius pulvinar ornare aliquet dui quis con' }
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
    }
}
</script>

<style scoped lang="scss">
div.container {
    width: 100%;
    height: fit-content;
}

.Skills {

    .title1 {
        text-align: center;
        margin-bottom: 35px;
    }

    .skills-wrapper {
        display: flex;
        flex-direction: column;
        align-items: center;

        .skill {
            max-width: 350px;
            width: 80vw;
            margin-bottom: 40px;
            background: linear-gradient(to bottom right, #E1E1E1, #e1e1e150);
            padding: 40px 3%;
            border-radius: var(--border-radius);
            box-shadow: 2px 2px 4px #e1e1e1da;
            color: var(--text-dark);

            .skill-header {
                display: flex;
                align-items: center;
                margin-bottom: 20px;

                .icon {
                    color: var(--primary-color)
                }

                .skill-title {
                    line-height: 1.2em;
                    color: var(--title-dark);
                    margin-left: 10px;
                }
            }

            &:last-child {
                margin-bottom: 0;
            }

            &.primaryBg {
                background: linear-gradient(#B126E2, #b026e283);
                color: var(--text-light);
                
                .icon {
                    color: var(--secondary-color)
                }
                .skill-title {
                    color: var(--title-light);
                }
            }
        }
    }
}

.Tools {
    background: linear-gradient(to bottom right, var(--primary-color), var(--secondary-color));
    color: var(--title-dark);
    font-weight: 600;
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    min-height: fit-content;
    padding-top: 4vw;
    padding-bottom: 0;

    .tool {
        display: flex;
        justify-content: center;
        align-items: center;
        width: 100%;
        max-width: 250px;
        background-color: #ffffff2f;
        height: fit-content;
        padding: 10px;
        border-radius: var(--border-radius);
        margin-bottom: 4vw;

        .tool-icon {
            display: block;
            margin-right: 9px;
            width: 50px;
            height: 50px;
            border: 1px solid var(--text-dark);
            border-radius: 50%;
            padding: 7px;
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
        margin-top: 60px;
        padding-top: 3vw;

        .tool {
            margin-bottom: 3vw;
        }
    }
}</style>