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
    color: #6e611e;
    text-decoration: none;
  }

  ul {
    margin-top: -1.5rem;
    padding-left: 4rem;
    padding-bottom: 2rem;
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
