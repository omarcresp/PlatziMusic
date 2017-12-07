<template>
  <div class="loading">
    <div class="loading-bar"></div>
    <div class="loading-bar"></div>
    <div class="loading-bar"></div>
    <div class="loading-bar"></div>
  </div>
</template>

<script>
export default {
  name: 'spinner'
}
</script>

<style scoped>
  .loading {
    margin-top: 50px;
  }

  .loading-bar {
    display: inline-block;
    width: 4px;
    height: 18px;
    border-radius: 4px;
    animation: loading 1s ease-in-out infinite;
  }
  .loading-bar:nth-child(1) {
    background-color: #35495e;
    animation-delay: 0;
  }
  .loading-bar:nth-child(2) {
    background-color: #35495e;
    animation-delay: 0.09s;
  }
  .loading-bar:nth-child(3) {
    background-color: #35495e;
    animation-delay: .18s;
  }
  .loading-bar:nth-child(4) {
    background-color: #35495e;
    animation-delay: .27s;
  }

  @keyframes loading {
    0% {
      transform: scale(1);
    }
    20% {
      transform: scale(1, 2.2);
    }
    40% {
      transform: scale(1);
    }
  }
</style>
