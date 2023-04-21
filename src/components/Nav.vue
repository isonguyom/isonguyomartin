<!-- eslint-disable vue/multi-word-component-names -->
<template>
    <nav class="Nav">
        <div class="hamburger-wrapper" @click="toggleMenu">
            <div class="hamburger" :class="{ active: menuIsActive }" />
        </div>
        <TransitionGroup tag="ul" class="menu" appear @enter="enter" @after-enter="afterEnter" v-if="menuIsActive">
            <li class="menu-item" v-for="item in menuItems" :key="item.name" @click="toggleMenu"><router-link
                    :to="{ path: '/', hash: item.hash }">
                    <Icon class="menu-item-icon" :icon="item.icon" width="25" /><span>{{ item.name }}</span>
                </router-link></li>
        </TransitionGroup>
    </nav>
</template>

<script>
import { Icon } from '@iconify/vue';
import gsap from 'gsap'

export default {
    components: { Icon },
    data() {
        return {
            menuIsActive: false,
            menuItems: [
                { name: 'Home', hash: '#home', icon: 'healthicons:home-alt-outline' },
                { name: 'Skills', hash: '#skills', icon: 'fluent:window-dev-edit-20-regular' },
                { name: 'Works', hash: '#projects', icon: 'ph:briefcase-light' },
                { name: 'Blog', hash: '#blog', icon: 'ph:article-light' },
                { name: 'Contact', hash: '#contact', icon: 'fluent-mdl2:contact' }
            ]
        }
    },

    methods: {
        toggleMenu() {
            this.menuIsActive = !this.menuIsActive
        },

        enter() {
            gsap.from('.menu-item', {
                duration: .7,
                stagger: .1,
                x: -50,
            })
        },
        afterEnter() {
            console.log('after enter')
        }
    }
}
</script>


<style scoped lang="scss">
nav {
    z-index: 2;
    position: fixed;
    top: 50%;
    right: 0.5em;
    transform: translate(0, -50%);
    -ms-transform: translate(0, -50%);
    display: none;

    .hamburger-wrapper {
        width: 35px;
        height: 30px;
        /*background-color: var(--primary-color);*/
        display: flex;
        justify-content: right;
        align-items: center;
        cursor: pointer;
        z-index: 2;

        .hamburger {
            color: var(--title-light);
            z-index: 2;
            position: absolute;
            background-color: var(--title-light);
            border-radius: 3px;
            width: 30px;
            height: 2px;
            display: flex;
            justify-content: right;
            align-items: center;
            transition: all 0.5s ease;

            &:before,
            &:after {
                content: '';
                height: 2px;
                border-radius: 3px;
                position: absolute;
                background-color: var(--title-light);
                transition: all 0.5s ease;
                will-change: transform;
            }

            &:before {
                transform: translateY(-7px);
                width: 25px;
            }

            &:after {
                transform: translateY(7px);
                width: 35px;
            }
        }

        &:hover .hamburger,
        &:hover .hamburger::before,
        &:hover .hamburger::after {
            background-color: var(--secondary-color);
        }

        .hamburger {
            &.active {
                width: 0;
            }

            &.active::before {
                transform: translateY(0) rotate(45deg);
            }

            &.active::after {
                width: 25px;
                transform: translateY(0) rotate(-45deg);
            }
        }
    }

    .menu {
        list-style: none;
        transition: all 1s ease;

        .menu-item {
            width: 70px;
            height: 70px;
            left: -60px;
            transition: all 1s ease;


            a {
                color: var(--title-light);
                width: 100%;
                height: inherit;
                background-color: var(--primary-color);
                border-radius: 50%;
                display: flex;
                align-items: center;
                justify-content: center;
                flex-wrap: wrap;
                transition: background-color 1s ease;
                padding: 7px;

                .menu-item-icon {
                    color: var(--secondary-color);
                    display: block;
                    margin-bottom: -10px;
                    transition: color 1s ease;
                }

                span {
                    width: 100%;
                    text-align: center;
                    font-size: 0.8rem;
                    transition: color 1s ease;
                }

                &:hover,
                &.router-link-active:focus,
                &.router-link-exact-active:focus {
                    background-color: var(--secondary-color);
                    color: var(--title-dark);


                    .menu-item-icon {
                        color: var(--title-dark);
                    }
                }
            }

            &:nth-child(2),
            &:nth-child(4) {
                left: -120px;
            }

            &:nth-child(3) {
                left: -180px;
            }
        }
    }
}

@media screen and (min-width: 768px) {
    nav {
        display: block;

        .hamburger-wrapper {
            position: absolute;
            top: 50%;
            right: 0;
            transform: translate(0, -50%);
            -ms-transform: translate(0, -50%);
        }
    }
}
</style>