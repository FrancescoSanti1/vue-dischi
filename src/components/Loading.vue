<template>
  <div class="container-loading">
      <div class="loading"></div>
  </div>
</template>

<script>
export default {
  name: 'Loading'
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

.container-loading {
    position: absolute;
    top: 0;
    right: 0;
    left: 0;
    bottom: 0;
    display: flex;
    justify-content: center;
    align-items: center;

    .loading {
        height: 80px;
        width: 80px;
        border-radius: 50%;
        border: 10px solid rgb(17, 104, 17);
        border-top-color: #1e2d3b;

        animation-name: rotate;
        animation-duration: 1s;
        animation-direction: normal;
        animation-iteration-count: infinite;
        animation-timing-function: linear;

        @keyframes rotate {
            100% {
                transform: rotate(360deg)
            }
        }
    }
}
</style>
