<!-- eslint-disable vue/multi-word-component-names -->
<template>
    <Transition name="btn" appear>
        <a class="btn" :href="link">{{ text }}</a>
    </Transition>
</template>

<script>
export default {
    props: ['text', 'link']
}
</script>

<style scoped lang="scss">
.btn {
    display: block;
    text-align: center;
    text-transform: capitalize;
    background: var(--primary-gradient);
    color: var(--title-light);
    max-width: 100%;
    padding: 0.7em;
    border-radius: var(--border-radius);
    box-shadow: var(--box-shadow);
    width: 70vw;
    transition: all 0.5s ease;

    &:hover {
        text-decoration: none;
        background-color: #ffec8e;
    }
}

@media screen and (min-width: 480px) {
    .btn {
        width: 45vw;
    }
}

@media screen and (min-width: 992px) {
    .btn {
        width: 25vw;
    }
}

.btn-enter-active,
.btn-leave-active {
    transition: all 0.5s ease;
}

.btn-enter-from,
.btn-leave-to {
    opacity: 0;
    transform: translateX(10px);
}
</style>
