<template>
    <nav class="Nav">
        <div class="hamburger-wrapper" @click="toggleMenu">
            <div class="hamburger" :class="{ active: menuIsActive }" />
        </div>
        <TransitionGroup tag="ul" class="menu" appear>
            <li></li>
        </TransitionGroup>
    </nav>
</template>

<script>
export default {
    data() {
        return {
            menuIsActive: false
        }
    },

    methods: {
        toggleMenu() {
            this.menuIsActive = !this.menuIsActive
        }
    }
}
</script>


<style scoped lang="scss">
nav {
    z-index: 2;
    position: absolute;
    top: 92%;
    right: 0.5em;

    .hamburger-wrapper {
        width: 35px;
        height: 30px;
        /*background-color: var(--primary-color);*/
        display: flex;
        justify-content: right;
        align-items: center;
        cursor: pointer;

        .hamburger {
            z-index: 2;
            position: absolute;
            background-color: var(--title-light);
            border-radius: 3px;
            width: 25px;
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
                width: 20px;
            }

            &:after {
                transform: translateY(7px);
                width: 30px;
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
                width: 20px;
                transform: translateY(0) rotate(-45deg);
            }
        }
    }
}

@media screen and (min-width: 768px) {
    nav {
        position: fixed;
        top: 50%;
        right: 0.5em;
        transform: translate(0, -50%);
        -ms-transform: translate(0, -50%);

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