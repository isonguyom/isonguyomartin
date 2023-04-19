<!-- eslint-disable vue/multi-word-component-names -->
<template>
    <section class="section-wrapper Blog">
        <h3 class="title1">I can also write</h3>
        <div class="posts-wrapper">
            <div class="post" v-for="post in posts" :key="post.title" :style="{ backgroundImage: 'url(' + `images/${post.image}` + ')'}">
                <a :href="post.link" class="post-title">{{ post.title }}</a>
                <p class="post-ecerpt">{{ post.ecerpt }}<a id="more" :href="post.link">...</a></p>
            </div>
        </div>
        <Button id="readBtn" link="#" text="Read more" />
    </section>
</template>

<script>
import Button from './Button.vue';

export default {
    // eslint-disable-next-line vue/no-reserved-component-names
    components: { Button },
    data() {
        return {
            posts: [
                {
                title: 'Article title', link: '', image: 'blog-img1.jpg', ecerpt: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Incidunt accusamus cumque voluptates dolorem. Eos natus, excepturi eum vel minus asperiores itaque consectetur esse alias sed labore rem at mollitia perferendis'
            },
                {
                title: 'Article title', link: '', image: 'blog-img2.jpg', ecerpt: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Incidunt accusamus cumque voluptates dolorem. Eos natus, excepturi eum vel minus asperiores itaque consectetur esse alias sed labore rem at mollitia perferendis'
            },
        ]
        }
    }
}
</script>

<style scoped lang="scss">
.Blog {
    background-color: var(--secondary-color);
    min-height: fit-content;

    .title1 {
        text-align: center;
    }

    .posts-wrapper {
        margin: 35px 0;
        display: flex;
            flex-direction: column;
            align-items: center;
        
        .post {
            max-width: 400px;
            width: 80vw;
            height: fit-content;
            background-size: cover;
            background-position: center;
            background-repeat: no-repeat;
            background-blend-mode: soft-light;
            background-color: #2b2b2bda;
            margin-bottom: 30px;
            padding: 5vw;
            text-align: center;
            color: var(--text-light);
            border-radius: var(--border-radius);
            transition: background 1s ease-in;

            .post-title {
                display: block;
                margin-bottom: 15px;
                color: var(--title-light);
                font-size: 1.2rem;
                font-weight: 600;

                &:hover {
                    color: var(--secondary-color);
                }
            }

            .post-ecerpt {

                #more {
                    font-size: 1.3rem;
                    letter-spacing: 3px;
                }
            }

            &:hover {
                background-color: #2b2b2bf6;
                background-blend-mode: darken;
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

        .posts-wrapper {
            flex-direction: row;
            justify-content: space-between;

            .post {
                max-width: 330px;
                width: 45vw;
                padding: 4.3vw;
            }
        }
    }
}

@media screen and (min-width: 992px) {
    .Blog {

        .posts-wrapper {

            .post {
                max-width: 430px;
                min-height: 300px;
                padding: 5vw;
                display: flex;
                flex-direction: column;
                justify-content: center;
            }
        }
    }
}
</style>