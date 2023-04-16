<template>
    <section class="section-wrapper">
        <Transition name="fade" appear>
            <h1>Page Not Found</h1>
        </Transition>
    </section>
</template>

<style scoped lang="scss">
.section-wrapper {
    display: flex;
    justify-content: center;
    align-items: center;

    h1 {
        color: red;
        transition: all 0.5s ease;
    }
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