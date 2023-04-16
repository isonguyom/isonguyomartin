<template>
    <a class="btn" :href="link">{{ text }}</a>
</template>

<script>
export default {
    props: ['text', 'link'],
    data() {
        return {

        }
    }
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
    border-radius: 10px;


    &:hover {
        text-decoration: none;
    }
}
</style>