<template>
  <section class="section-wrapper Loader-wrapper">
    <div class="loader"></div>
  </section>
</template>

<style scoped lang="scss">
.Loader-wrapper {
  display: flex;
  align-items: center;
  justify-content: center;

  .loader {
    height: 60px;
    width: 60px;
    border: 3px solid var(--primary-color);
    border-radius: 50%;
    animation: loadingRotate 3s ease -1s infinite;
  }
}

@keyframes loadingRotate {
  100% {
    transform: scale(2);
  }
}
</style>
