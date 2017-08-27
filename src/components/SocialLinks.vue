<template>
  <ul>
    <li v-for="link in blok.links">
      <a :href="link.url.url"><img class="social-icon" :src="'data:image/svg+xml;utf8,'+link.svg" :alt="link.title"></a>
    </li>

  </ul>
</template>

<script>
export default {
  props: ['blok']
}
</script>

<style lang="scss" scoped>
  ul {
    margin: 0 auto;
    padding-top: 5%;
    color: white;
    margin-left: auto;
    margin-right: auto;
    text-align: center;

    img {
      height: 70%;
      max-width: 32px;
    }


    li {
      display: inline-block;
      padding-right: 2rem ;
    }
  }
</style>
