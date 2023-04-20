<template>
    <section class="section-wrapper">
        <Transition name="blink" appear>
            <Icon class="icon" icon="ph:warning" width="100" />
        </Transition>
        <Transition name="fade" appear>
            <h1>Page Not Found</h1>
        </Transition>
    </section>
</template>

<script setup>
import { Icon } from '@iconify/vue';
</script>

<style scoped lang="scss">
.section-wrapper {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    color: var(--text-dark);

    .icon {
        color: rgb(253, 178, 178);
        transition: opacity 2s ease;
    }

    h1 {
        font-size: 2rem;
        transition: all 2s ease;
        text-transform: capitalize;
    }
}

.blink-enter-active,
.blink-leave-active {
    transition: opacity 1s ease;
}

.blink-enter-from,
.blink-leave-to {
    opacity: 0;
}

.fade-enter-active,
.fade-leave-active {
    transition: all 0.5s ease;
}

.fade-enter-from,
.fade-leave-to {
    opacity: 0;
    transform: translateX(10px);
}
</style>