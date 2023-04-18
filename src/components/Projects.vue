<!-- eslint-disable vue/multi-word-component-names -->
<template>
    <section class="section-wrapper Projects">

        <div class="projects-inner">
            <div class="projects-header">
                <h3 class="title1">My projects</h3>
                <p class="projects-text">
                    Lorem ipsum dolor sit amet consectetur adipisicing elit. Perspiciatis veritatis, aperiam, placeat
                    voluptatem
                    repellendus aut illo vitae unde ullam fugit, autem quisquam? Architecto repellendus, quas assumenda
                    aspernatur praesentium necessitatibus quisquam.</p>
            </div>

            <div class="project" v-for="project in projects" :key="project.name">
                <img class="project-img" :src="`images/${project.image}.png`" :alt="project.name">
                <a :href="project.link" class="project-caption">{{ project.caption }}</a>
            </div>
        </div>

        <Button id="seeBtn" link="https://github.com/isonguyom?tab=repositories" text="See more" />
    </section>
</template>

<script>
import Button from './Button.vue';

export default {
    // eslint-disable-next-line vue/no-reserved-component-names
    components: { Button },
    data() {
        return {
            projects: [
                { name: 'Projectrum', caption: 'Projectrum project manager', image: 'img-projectrum', link: 'https://projectrum.netlify.app/#/' },
                { name: 'Tiptop', caption: 'Tiptop design agency website', image: 'img-tiptop', link: 'https://tiptopdesign.netlify.app/' },
                { name: 'World Citizen', caption: 'World citizen website', image: 'img-world-citizen', link: 'https://worldcitizendotorg.netlify.app/' },
                { name: 'Quiz App', caption: 'JavaScript Quiz App', image: 'img-js-quiz-app', link: 'https://isonguyom.github.io/quizAppJs/' },
                { name: 'Countdown Timer', caption: 'Vuejs countdown timer', image: 'img-countdown-timer', link: 'https://isonguyom.github.io/countdown-timer/' }
            ]
        }
    }
}
</script>

<style scoped lang="scss">
.Projects {
    background-color: var(--title-dark);

    .projects-inner {

        .projects-header {
            width: 100%;
            text-align: center;
            margin-bottom: 50px;
            
            .title1 {
                margin-bottom: 10px;
            }
            .projects-text {
                color: var(--text-light);
            }
        }

        .project {
            display: block;
            max-width: 400px;
            width: 80vw;
            border-radius: 5px;
            padding: 10px;
            background-color: #ffffff2d;
            margin-bottom: 40px;
            margin: 0 auto 40px;

            .project-img {
                border-radius: 5px 5px 0 0;
                display: block;
            }

            .project-caption {
                display: block;
                background-color: #555353;
                color: var(--title-light);
                text-align: center;
                width: 100%;
                padding: 10px;
                border-radius: 0 0 5px 5px;
                transition: all 0.5s ease;
                text-transform: capitalize;

                &:hover {
                    color: var(--secondary-color);
                    text-decoration: none;
                }
            }
        }
    }

    #seeBtn {
        margin: auto;
    }
}

@media screen and (min-width: 768px) {
    .Projects {

        .projects-inner {
            width: 100%;
            display: flex;
            flex-wrap: wrap;
            margin-bottom: 50px;

            .projects-header {
                width: 70%;
                margin-left: auto;
                margin-right: auto;
            }

            .project {
                width: 48%;
            }
        }
    }
}

@media screen and (min-width: 992px) {
    .Projects {

        .projects-inner {
           justify-content: space-between;
           padding-top: 100px;

            .projects-header {
                width: 33%;
                text-align: left;
                margin-left: 0;
                margin-right: 0;
                display: flex;
                flex-direction: column;
                justify-content: center;
                padding-right: 25px;
                max-width: 250px;

                .title1 {
                    text-align: left;
                }
            }

            .project {
                width: 33%;
                max-width: 300px;

                &:nth-child(3) {
                    top: -100px;
                }
            }
        }
    }
}
</style>