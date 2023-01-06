<template>
  <div>
    <h2>Instagram</h2>
    <div class="square_contents">
      <a v-for="(n,i) in response.details.media_url" :key=i href="https://www.instagram.com/" target="_blank">
        <img :src=n>
      </a>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ $axios }) {
    return {
      response: await $axios.$get('/rcms-api/1/instagram/instagram'),
    };
  },
};
</script>

<style>
.square_contents {
  display: flex;
  flex-wrap: wrap;
  width:720px;
}
.square_contents a {
  display: block;
  position: relative;
  width: 31%;
  margin: 1%;
}
.square_contents a::before {
  content: "";
  display: block;
  padding-top: 100%;
}
.square_contents img {
  position: absolute;
  width: 100%;
  height: 100%;
  top: 0;
  object-fit: cover;
}
</style>
