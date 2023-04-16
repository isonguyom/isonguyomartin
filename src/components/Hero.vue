<template>
    <section class="section-wrapper Hero">
        <div class="hero-text">
            <h1 class="hero-caption caption">Frontend Developer</h1>
            <p class="para hero-para">Lorem, ipsum dolor sit amet consectetur adipisicing elit. Ipsa vero iste ut sed asperiores nam saepe nulla amet. Necessitatibus repellendus magnam deserunt assumenda esse aspernatur et ducimus error consequatur dicta?</p>
        <div class="socials">
            <a v-for="(link, key) in socialLinks" :key="link.name" class="social-link" :href="link.link">{{ link.icon }}</a>
            <a class="social-link" href="http://" target="_blank" rel="noopener noreferrer">d</a>
        </div>
        </div>
    </section>
</template>

<script>
export default {
    data() {
        return {
            socialLinks: [
                {name: 'Github', icon: 'G', link: 'https://github.com/isonguyom'},
                {name: 'Behance', icon: 'Be', link: 'https://www.behance.net/martinisonguyo'},
                {name: 'Twitter', icon: 't', link: 'https://twitter.com/IsonguyoM'},
            ]
        }
    }
}
</script>


<style scoped lang="scss">
.Hero {
    background: url('images/martin-grayscale.png') no-repeat center;
    background-size: contain;
    background-color: #1b1b1b;
    background-blend-mode: soft-light;

    .hero-caption {
        color: var(--primary-color);
    }

    .hero-para {
        color: var(--text-light);
    }

    .socials {
        margin: 50px 0;
        .social-link {
            display: inline-block;
            color: var(--title-light);
            border: 1px solid var(--title-light);
            border-radius: 50%;
            width: 40px;
            height: 40px;
            display: inline-flex;
            align-items: center;
            justify-content: center;
            margin-right: 1.5em;

            &:hover {
                text-decoration: none;
                color: #fff;
                border-color: #fff;
            }
        }
    }
}
</style>