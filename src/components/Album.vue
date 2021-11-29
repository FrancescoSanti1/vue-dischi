<template>
  <div class="product">
      <div class="img-container">
          <img :src="details.poster" :alt="details.title">
      </div>
      <h3>{{details.title}}</h3>
      <div class="author">{{details.author}}</div>
      <div class="year">{{details.year}}</div>
  </div>
</template>

<script>
export default {
  name: 'Album',
  props: {
      details: Object
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

.product {
    background-color: #2e3a46;
    width: 18%;
    text-align: center;
    padding: 20px;
    margin: 0 1% 20px 1%;

    .img-container {
        padding-top: 100%;
        position: relative;
        overflow: hidden;

        img {
            max-width: 100%;
            position: absolute;
            top: 0;
            left: 0;
        }
    }

    h3 {
        color: white;
        text-transform: uppercase;
        margin: 20px 0;
    }

    .author, .year {
        color: #787e7c;
    }

    .author {
        font-size: 18px;
    }

    .year {
        font-size: 14px;
    }
}

</style>
