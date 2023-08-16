<!-- eslint-disable vue/multi-word-component-names -->
<template>
    <section class="section-wrapper Blog">
        <h3 class="title1">I can also write</h3>
        <div class="posts-wrapper">
            <div class="post" v-for="post in posts" :key="post.title">
                <img class="post-img" :src="`images/${post.image}`" :alt="post.title">
                <div class="post-text">
                    <a :href="post.link" class="post-title">{{ post.title }}</a>
                    <p class="post-ecerpt">{{ post.ecerpt }}<a id="more" :href="post.link">...</a></p>
                    <div class="post-footer">
                        <a class="post-platform" href="">{{ post.platform }}</a><span class="post-date">{{ post.date
                        }}</span>
                    </div>
                </div>
            </div>
        </div>
        <Button id="readBtn" link="#" text="Read more" />
    </section>
</template>

<script>
// import { gsap } from "gsap";
// import { ScrollTrigger } from "gsap/ScrollTrigger";

// gsap.registerPlugin(ScrollTrigger);
import Button from './Button.vue';

export default {
    // eslint-disable-next-line vue/no-reserved-component-names
    components: { Button },
    data() {
        return {
            posts: [
                {
                    title: 'HOW TO BUILD A MEVN APP WITH VITE FRONTEND (PART 1)', link: 'https://dev.to/isonguyom/mevn-257p', image: 'mevn-vite_cover.png',
                    platform: 'dev.to', platformLink: 'https://dev.to/isonguyom', date: '7 Aug 2023',
                    ecerpt: 'Full-stack web development describes the process of building the frontend and backend of a web application'
                },
                {
                    title: 'HOW TO BUILD A MEVN APP WITH VITE FRONTEND (PART 2)', link: '', image: 'mevn-vite_cover.png',
                    platform: 'dev.to', platformLink: 'https://dev.to/isonguyom', date: '16 Aug 2023',
                    ecerpt: 'We want our applications to interact with each other and for our frontend to be accessible only through'
                },
                {
                    title: 'HOW TO BUILD A MEVN APP WITH VITE FRONTEND (PART 3)', link: '', image: 'mevn-vite_cover.png',
                    platform: 'dev.to', platformLink: 'https://dev.to/isonguyom', date: '17 Aug 2023',
                    ecerpt: 'Congratulations! You have successfully developed your MEVN CRUD application'
                },
            ]
        }
    },

    // mounted() {
    //     gsap.from(".post", {
    //         scrollTrigger: ".post", // start the animation when ".box" enters the viewport (once)
    //         // scrub: 1,
    //         delay: .5,
    //         duration: 1,
    //         y: 100,
    //         opacity: 1,
    //         stagger: .2
    //     });
    // }
}
</script>

<style scoped lang="scss">
.Blog {
    min-height: fit-content;

    .posts-wrapper {
        margin: 35px 0;
        display: flex;
        display: -webkit-flex;
        flex-direction: column;
        align-items: center;

        .post {
            max-width: 400px;
            width: 80vw;
            height: fit-content;
            background: linear-gradient(to right, #300441, #ffec8e33);
            margin-bottom: 30px;
            border-radius: var(--border-radius);
            transition: all 0.5s ease-in;
            border-radius: var(--border-radius);

            .post-text {
                padding: 2em;

                .post-title {
                    display: block;
                    margin-bottom: 15px;
                    color: var(--title-light);
                    font-size: 1.5rem;
                    font-weight: 600;

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
                    color: #a7a4a4d0;
                }

            }
        }
    }

    #readBtn {
        margin-left: auto;
        margin-right: auto;
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

            .post {
                max-width: 330px;
                width: 45vw;
            }
        }
    }
}

@media screen and (min-width: 992px) {
    .Blog {

        .posts-wrapper {

            .post {
                max-width: 430px;
                width: 28vw;
                display: flex;
                display: -webkit-flex;
                flex-direction: column;
                justify-content: center;
            }
        }
    }
}
</style>