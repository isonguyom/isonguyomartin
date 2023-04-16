<template>
    <Transition name="btn" appear>
        <a class="btn" :href="link">{{ text }}</a>
    </Transition>
</template>

<script>
export default {
    props: ['text', 'link'],
}
</script>

<style scoped lang="scss">
.btn {
    display: block;
    text-align: center;
    text-transform: capitalize;
    background-color: var(--primary-color);
    color: var(--title-light);
    max-width: 100%;
    padding: 1em;
    border-radius: 7px;
    width: 70vw;
    transition: all 0.5s ease;


    &:hover {
        text-decoration: none;
        background-color: var(--secondary-color);
        color: var(--title-dark);
    }
}

@media screen and (min-width: 480px) {
    .btn {
        width: 50vw;
    }
}

@media screen and (min-width: 992px) {
    .btn {
        width: 30vw;
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