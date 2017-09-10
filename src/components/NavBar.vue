<template>
  <nav>
    <ul>
      <li v-for="item in blok.nav_items">
        <a :href="item.href.url">{{item.text}}</a>
      </li>

    </ul>
  </nav>
</template>

<script>
export default {
  props: ['blok']
}
</script>

<style lang="scss" scoped>

 nav {
    text-align: right;
  }

  a {
    color: rgb(247, 221, 73);
    text-decoration: none;
    font-weight: bold;
    font-size: 1.5rem;
  }

  ul {
    margin-top: -1.5rem;
    padding-left: 4rem;
    margin-bottom: 0;
    display: flex;
    justify-content: flex-end;

    li {
      list-style-type: none;
      padding-left: 2rem;
    }

    @media (min-width: 410px) {
      padding-right: 20px;
    }
  }
</style>
